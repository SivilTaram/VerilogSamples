```verilog
module and_gate(A, B, out);
    input A, B;
    output out;
    mux m(1'b0, A, B, out);
endmodule

module mux(a, b, in, out);
    input a, b, in;
    output out;
    assign out = in ? b : a;
endmodule
```
