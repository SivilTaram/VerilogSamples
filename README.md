```verilog
module or_gate(A, B, out);
    input A, B;
    output out;
    mux m(A, 1'b1, B, out);
endmodule

module mux(a, b, in, out);
    input a, b, in;
    output out;
    assign out = in ? b : a;
endmodule
```
