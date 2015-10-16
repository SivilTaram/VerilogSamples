```verilog
	assign out = cp == 2'b00 ? input_a + input_b:
	             cp == 2'b01 ? input_a - input_b:
				 cp == 2'b10 ? input_a & input_b:
				 cp == 2'b11 ? input_a | input_b;
```

```verilog
    initial begin
	    // Initialize Inputs
		clk = 0;
		rs = 0;
		
		#20
		wd = 100;
	end
```

```verilog
	reg [31:0] _reg[32];	
	always @(posedge clk) begin
		if (we) begin
			_reg[rd] <= wd;
		end
	end
```

```verilog
integer [31:0] i;
	initial begin
		for (i = 0; i < 32; i = i + 1) begin
		    _reg[i] = 0;
		end
	end
```

```verilog
	integer i;
	initial begin
		for (i = 0; i < 32; i++) begin
		    _reg[i] = 0;
		end
	end
```
