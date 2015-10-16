```verilog
 module up_counter_load    (
      out      ,  // Output of the counter
      data     ,  // Parallel load for the counter
      load     ,  // Parallel load enable
      enable   ,  // Enable counting
      clk      ,  // clock input
      reset       // reset input
    );
    //----------Output Ports--------------
    output [7:0] out;
    //------------Input Ports-------------- 
    input [7:0] data;
    input load, enable, clk, reset;
    //------------Internal Variables--------
    reg [7:0] out;
    //-------------Code Starts Here-------
    always @(posedge clk)
      if (reset) begin
        out <= 8'b0 ;
      end else if (load) begin
        out <= data;
      end else if (enable) begin
        out <= out + 1;
      end
  endmodule

  testbench:
   module testcounter;
      // Inputs
      reg [7:0] data;
      reg load;
      reg enable;
      reg clk;
      reg reset;
      // Outputs
      wire [7:0] out;

      // Instantiate the Unit Under Test (UUT)
      up_counter_load uut (
        .out(out), 
        .data(data), 
        .load(load), 
        .enable(enable), 
        .clk(clk), 
        .reset(reset)
      );

      // 定义时钟信号
      always #5 clk = ~clk;

      initial begin
        // Initialize Inputs
        data = 0;
        load = 0;
        enable = 0;
        clk = 0;
        reset = 1;  // (仔细！)

        // 调整各个参数进行测试（请务必仔细）
        #10;
        load = 1'b1;
        data = 8'h3;
        enable = 1'h1;

        #10;
        reset = 1'b0;

        #30;
        load = 1'b0;

        #20;
        data = 8'ha;

        #20;
        load = 1'b1;

        #10;
        load = 1'b0;

      end

    endmodule
```
