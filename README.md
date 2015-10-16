1
```verilog
module EXT(
    input [15:0] imm,
    input [1:0] EOp,
    output [31:0] ext
    );
	assign ext = ( EOp == 2'b00 )? { {16{imm[15]}},imm }:{ 16'b0,imm };
endmodule

```
2
```verilog
module MUX_ALU_B(
    input [31:0] RData2,
    input [31:0] extimm,
    input ALUSrc,
    output [31:0] B
    );
	assign B = ( ALUSrc==0 )? RData2 : extimm;
endmodule

```
3
```verilog
module PC(
    input [31:2] NPC,		
    input clk,
    input reset,
    output [31:2] PC
    );
	 ? [31:2] rpc;
	 assign PC = rpc;
	 
	 always@(posedge clk,posedge reset)
	 begin 
			if(reset)				
				rpc <= 30'b0000_0000_0000_0000_0011_0000_0000_00;
			else
				rpc <= NPC;
	 end
endmodule
```
4
```verilog
module MUX_GPR_WriteData(
	 input [31:0] R,
	 input [31:0] dout,
	 input [1:0] MemtoReg,
	 output [?:0] WriteData
	 );
	 assign WriteData = ( MemtoReg==2'b00 )? R:  dout;
endmodule
```
5
```verilog
module ALU(
    input [31:0] A,
    input [31:0] B,
    input [1:0] ALUCtr,
    output[?:0] R,
    );
	 assign R = ( ALUCtr == 2'b00 )? (A & B):  (A | B);
endmodule
```
6
```verilog
module NPC(
    input [31:2] PC,
    output [?:0] JAL_WB
    );
	 assign JAL_WB = {PC+1,2'b0};
endmodule
```
7
```verilog
module im(
    input [11:2] addr,
    output [31:0] dout
    );
		
	 reg [31:0] im[1023:0] ;
	 
	 assign dout = im[addr];
		
	 initial
    $readmemh ( "code.txt",im);
endmodule
```
8
```verilog
module im_8k(
    input [11:2] addr,
    output [31:0] dout
    );
	 reg [31:0] im[?:0] ;
	 assign dout = im[addr];
	 initial
    $readmemh ( "code.txt",im);
endmodule
```
