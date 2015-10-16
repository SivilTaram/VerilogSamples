```verilog
	assign out = cp == 2'b00 ? input_a + input_b:
	             cp == 2'b01 ? input_a - input_b:
				 cp == 2'b10 ? input_a & input_b:
				 cp == 2'b11 ? input_a | input_b;
```
