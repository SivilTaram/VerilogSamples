1
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
2
```verilog

module driver();
    
    reg clk, reset, enable;
    wire [7:0] out;

    counter cnt(
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

module counter(out, enable, clk, reset);
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
3
```verilog

module driver();
    
    reg clk, reset, enable;
    reg [7:0] load;
    wire [7:0] out;

    counter cnt(
        .out(out),
        .load(load),
        .enable(enable),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        enable = 1'b1;
        clk = 1'b0;
        reset = 1'b1;
        load = 8'b00110011;
    end
    
    initial begin
        #10  reset = 1'b0;
        #20  reset = 1'b1;
        #30  reset = 1'b0;
    end
endmodule

module counter(out, load, enable, clk, reset);
    input enable, clk, reset;
    input [7:0] load;
    output reg [7:0] out;
    
    always @(posedge clk) begin
        if (reset) begin
            out <= load;
        end else if (enable) begin
            out <= out + 1;
        end
    end
endmodule
```
4
```verilog

module driver();
    
    reg clk, reset, enable;
    reg [7:0] load;
    wire [7:0] out;

    counter cnt(
        .out(out),
        .load(load),
        .enable(enable),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        enable = 1'b1;
        clk = 1'b0;
        reset = 1'b1;
        load = 8'b00110011;
    end
    
    initial begin
        #10  reset = 1'b0;
        #20  reset = 1'b1;
        #30  reset = 1'b0;
    end
endmodule

module counter(out, load, enable, clk, reset);
    input enable, clk, reset;
    input [7:0] load;
    output reg [7:0] out;
    
    always @(posedge clk) begin
        if (reset) begin
            out <= load;
        end else if (enable) begin
            out <= out + 1;
        end
    end
endmodule
```
5
```verilog
module driver();
    
    reg clk, reset, up_down;
    wire [7:0] out;

    counter cnt(
        .out(out),
        .up_down(up_down),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b1;
        up_down = 1'b1;
    end
    
    initial begin
        #10  reset = 1'b0;
        #100 up_down = 1'b0;
    end
endmodule

module counter(out, up_down, clk, reset);
    output [7:0] out;
    input up_down, clk, reset;
    reg [7:0] out;
    always @(posedge clk) begin
        if (reset) begin
            out <= 8'b0 ;
        end else if (up_down) begin
            out <= out + 1;
        end else begin
            out <= out - 1;
        end
    end
endmodule 
```
6
```verilog

module driver();
    
    reg clk, reset, up_down;
    wire [7:0] out;

    counter cnt(
        .out(out),
        .up_down(up_down),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b1;
        up_down = 1'b1;
    end
    
    initial begin
        #10  reset = 1'b0;
        #100 up_down = 1'b0;
    end
endmodule

module counter(out, up_down, clk, reset);
    output [7:0] out;
    input up_down, clk, reset;
    reg [7:0] out;
    always @(posedge clk) begin
        if (reset) begin
            out <= 8'b0 ;
        end else if (up_down) begin
            out <= out + 1;
        end else begin
            out <= out - 1;
        end
    end
endmodule 
```
7
```verilog
module driver();
    
    reg clk, reset, up_down;
    reg [7:0] load;
    wire [7:0] out;

    counter cnt(
        .out(out),
        .load(load),
        .up_down(up_down),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b1;
        up_down = 1'b1;
        load = 8'b00000010;
    end
    
    initial begin
        #10  reset = 1'b0;
        #100 up_down = 1'b0;
    end
endmodule

module counter(out, load, up_down, clk, reset);
    output [7:0] out;
    input up_down, clk, reset;
    input [7:0] load;
    reg [7:0] out;
    always @(posedge clk) begin
        if (reset) begin
            out <= load ;
        end else if (up_down) begin
            out <= out + 1;
        end else begin
            out <= out - 1;
        end
    end
endmodule 
```
8
```verilog

module driver();
    
    reg clk, reset, up_down;
    reg [7:0] load;
    wire [7:0] out;

    counter cnt(
        .out(out),
        .load(load),
        .up_down(up_down),
        .clk(clk),
        .reset(reset)
    );
    
    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b1;
        up_down = 1'b1;
        load = 8'b00000010;
    end
    
    initial begin
        #10  reset = 1'b0;
        #100 up_down = 1'b0;
    end
endmodule

module counter(out, load, up_down, clk, reset);
    output [7:0] out;
    input up_down, clk, reset;
    input [7:0] load;
    reg [7:0] out;
    always @(posedge clk) begin
        if (reset) begin
            out <= load ;
        end else if (up_down) begin
            out <= out + 1;
        end else begin
            out <= out - 1;
        end
    end
endmodule 
```
