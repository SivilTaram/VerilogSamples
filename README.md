```verilog
module driver();
    
    reg clk, reset, enable;
    wire [7:0] out;

    up_counter cnt(
        .out(out),
        .enable(enable),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        enable = 1'b1;
        clk = 1'b0;
        reset = 1'b1;
    end
    
    initial begin
        #10  reset = 1'b0;
        #20  reset = 1'b1;
        #30  reset = 1'b0;
    end
endmodule

module up_counter(out, enable, clk, reset);
    input enable, clk, reset;
    output reg [7:0] out;
    
    always @(posedge clk) begin
        if (reset) begin
            out <= 8'b0 ;
        end else if (enable) begin
            out <= out + 1;
        end
    end
endmodule
```
