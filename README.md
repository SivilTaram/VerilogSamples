```verilog
module nor_gate(A, B, out);
    input A, B;
    output out;
    wire t;
    mux m1(A, 1'b1, B, t);
    mux m2(1'b1, 1'b0, t, out);
endmodule

module mux(a, b, in, out);
    input a, b, in;
    output out;
    assign out = in ? b : a;
endmodule
```
