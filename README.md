第一次题目，第二题，选择题，何涛
============================

### No.1

(c) 阅读如下的代码，variable 的实例 var 的 _var 的值在哪个时刻第一次变为 8'b11111111 ?

A 10ns, B 22ns, C 32ns, D 35ns

```verilog
module driver();
    
    reg clk, reset;
    variable var(
        .reset(reset),
        .clk(clk)
    );

    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
    end
    
    initial begin
        #10  reset = 1'b1;
        #22  reset = ~reset;
    end
    
endmodule

module variable(reset, clk);
    input reset;
    input clk;
    
    reg  [7:0] _var;
    
    always @(posedge clk or reset) begin
        if(reset) _var = 8'b0;
        else      _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.2

(D) 阅读如下的代码，第 33 ms 时，variable 的实例 var 的 _var 的值是？

A 8'b01010101, B 8'b101010101, C 8'b000000000, D 8'b11111111

```verilog
module driver();
    
    reg clk, reset;
    variable var(
        .reset(reset),
        .clk(clk)
    );

    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
    end
    
    initial begin
        #10  reset = 1'b1;
        #22  reset = ~reset;
    end
    
endmodule

module variable(reset, clk);
    input reset;
    input clk;
    
    reg  [7:0] _var;
    
    always @(posedge clk or reset) begin
        if(reset) _var = 8'b0;
        else      _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.3

(A) 阅读如下的代码，variable 的实例 var 的 _var 的值在哪个时刻第一次变为 8'b11111111 ?

A 45ns, B 32ns, C 20ns, D 10ns 

```verilog
module driver();
    
    reg clk, reset, enable;
    variable var(
        .reset(reset),
        .clk(clk),
        .enable(enable)
    );

    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
        enable = 1'b1;
    end
    
    initial begin
        #10  reset = 1'b1;
             enable = 1'b0;
        #22  reset = ~reset;
        #10  enable = 1'b1;
    end
    
endmodule

module variable(reset, clk, enable);
    input reset;
    input clk;
    input enable;
    
    reg  [7:0] _var;
    
    always @(posedge clk or reset) begin
        if(reset)           _var = 8'b0;
        else if(enable)     _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.4

(C) 阅读如下的代码，第 33 ms 时，variable 的实例 var 的 _var 的值是？

A 8'b01010101, B 8'b101010101, C 8'b000000000, D 8'b11111111

```verilog
module driver();
    
    reg clk, reset, enable;
    variable var(
        .reset(reset),
        .clk(clk),
        .enable(enable)
    );

    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
        enable = 1'b1;
    end
    
    initial begin
        #10  reset = 1'b1;
             enable = 1'b0;
        #22  reset = ~reset;
        #10  enable = 1'b1;
    end
    
endmodule

module variable(reset, clk, enable);
    input reset;
    input clk;
    input enable;
    
    reg  [7:0] _var;
    
    always @(posedge clk or reset) begin
        if(reset)           _var = 8'b0;
        else if(enable)     _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.5

(C) 阅读如下的代码，下列哪一个时刻 variable 的实例 var 的 _var 的值是 0'b10101010 ?

A 1ns, B 21ns, C 41ns, D 61ns

```verilog
module driver();
    
    reg clk, reset, enable;
    variable var(
        .clk(clk),
        .enable(enable)
    );

    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
        enable = 1'b1;
    end
    
    initial begin
        #10  enable = 1'b1;
        #22  enable = 1'b0;
        #22  enable = 1'b1;
    end
    
endmodule

module variable(clk, enable);
    input clk;
    input enable;
    
    reg  [7:0] _var;
    
    always @(posedge clk) begin
        if(enable) _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.6

(D) 阅读如下的代码，下列哪一个时刻 variable 的实例 var 的 _var 的值会发生变化 ?

A 20ns, B 35ns, C 50ns, D 65ns

```verilog
module driver();
    
    reg clk, reset, enable;
    variable var(
        .clk(clk),
        .enable(enable)
    );

    always #5 clk = ~clk;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
        enable = 1'b1;
    end
    
    initial begin
        #10  enable = 1'b1;
        #22  enable = 1'b0;
        #22  enable = 1'b1;
    end
    
endmodule

module variable(clk, enable);
    input clk;
    input enable;
    
    reg  [7:0] _var;
    
    always @(posedge clk) begin
        if(enable) _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.7

(B) 阅读如下的代码，下列哪一个时刻 variable 的实例 var 的 _var 的值会发生变化 ?

A 45ns, B 35ns, C 25ns, D 15ns

```verilog
module driver();
    
    reg clk, reset, enable;
    variable var(
        .clk(clk),
        .enable(enable)
    );

    always #5 clk = ~clk;
    always #8 enable = ~enable;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
        enable = 1'b1;
    end
endmodule

module variable(clk, enable);
    input clk;
    input enable;
    
    reg  [7:0] _var;
    
    always @(posedge clk) begin
        if(enable) _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

### No.8

(A) 阅读如下的代码，下列哪一个时刻 variable 的实例 var 的 _var 的值是 0'b01010101 ?

A 41ns, B 31ns, C 21ns, D 11ns

```verilog
module driver();
    
    reg clk, reset, enable;
    variable var(
        .clk(clk),
        .enable(enable)
    );

    always #5 clk = ~clk;
    always #8 enable = ~enable;
    
    initial begin
        clk = 1'b0;
        reset = 1'b0;
        enable = 1'b1;
    end
endmodule

module variable(clk, enable);
    input clk;
    input enable;
    
    reg  [7:0] _var;
    
    always @(posedge clk) begin
        if(enable) _var = ~_var;
    end
    
    initial begin
        _var = 8'b01010101;
    end
endmodule
```

