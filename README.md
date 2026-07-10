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
## Output Waveform
<img width="1364" height="732" alt="IMG_20260710_111427 jpg" src="https://github.com/user-attachments/assets/1381e383-7031-451e-b47c-8e88932038ba" />

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
## Output Waveform
<img width="1364" height="732" alt="IMG_20260710_111747 jpg" src="https://github.com/user-attachments/assets/d041c5f9-bae5-4981-bb0f-2e191f0b7ef4" />

## 3. 4-Bit Register
### Theory
A register is a collection of flip-flops used to store multiple bits of data.
| Clock Edge | Input D[3:0] | Output Q[3:0] |
|------------|--------------|---------------|
|  ↑         | Data Input   | Stored Data   |
### Verilog Code
```verilog
module register4(
    input clk,
    input [3:0] d,
    output reg [3:0] q
);

always @(posedge clk)
begin
    q <= d;
end

endmodule
```
## Output Waveform
<img width="1364" height="728" alt="IMG_20260710_112307 jpg" src="https://github.com/user-attachments/assets/48772f8b-c9d0-4cf0-94f6-27d7f3de680d" />

## 4. 4-Bit Up Counter
### Theory
A counter changes its state on every clock pulse. A 4-bit up counter counts from 0000 to 1111.
### Count Sequence 
| Clock Pulse | Count |
|-------------|-------|
| 0           | 0000  |
| 1           | 0001  |
| 2           | 0010  |
| 3           | 0011  |
| 4           | 0100  |
| ---         | ---   |
| 15          | 1111  |
### Verilog Code 
```verilog
module up_counter(
    input clk,
    output reg [3:0] count
);

initial
begin
    count = 4'b0000;
end

always @(posedge clk)
begin
    count <= count + 1;
end

endmodule
```
### Output Waveform

<img width="1364" height="724" alt="IMG_20260710_113705 jpg" src="https://github.com/user-attachments/assets/4e3f3e76-65e3-4ab4-9335-3e56113c48d0" />



