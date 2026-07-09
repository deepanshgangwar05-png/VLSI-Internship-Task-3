# VLSI-Internship-Task-3
## Verilog RTL Design of Sequential Circuits and Flip-Flops
### 📌 Objective
The objective of this task is to design and simulate basic sequential circuits using Verilog HDL. Sequential circuits store information and operate based on clock signals. This task covers Flip-Flops, Registers, Counters, Testbenches, and Waveform Analysis.

## 🛠 Tools Used
- Verilog HDL
- EDA Playground
- Icarus Verilog
- GTKWave
- GitHu
## 1. D Flip-Flop
### Theory
A D Flip-Flop stores one bit of data. On every positive edge of the clock signal, the output Q follows the input D.
| Clock Edge | D | Q(next) |
|------------|---|---------|
|  ↑         | 0 |  0      |
|  ↑         | 1 |  1      |
### Verilog Code
```verilog
module d_ff(
    input clk,
    input d,
    output reg q
);

always @(posedge clk)
begin
    q <= d;
end

endmodule
```
## 2. JK Flip-Flop
### Theory
JK Flip-Flop removes the invalid state of SR Flip-Flop and can hold, set, reset, or toggle the output.
| J | K |  Q(next)  |
|---|---|-----------|
| 0 | 0 | No Change |
| 0 | 1 | Reset     |
| 1 | 0 | Set       |
| 1 | 1 | Toggle    |
### Verilog Code
```verilog
module jk_ff(
    input clk,
    input j,
    input k,
    output reg q
);

always @(posedge clk)
begin
    case({j,k})
        2'b00: q <= q;
        2'b01: q <= 0;
        2'b10: q <= 1;
        2'b11: q <= ~q;
    endcase
end

endmodule
```
