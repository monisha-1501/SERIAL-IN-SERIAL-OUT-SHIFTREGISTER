# SERIAL-IN-SERIAL-OUT-SHIFTREGISTER

**AIM:**

To implement  SISO Shift Register using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**SISO shift Register**

A Serial-In Serial-Out shift register is a sequential logic circuit that allows data to be shifted in and out one bit at a time in a serial manner. It consists of a cascade of flip-flops connected in series, forming a chain. The input data is applied to the first flip-flop in the chain, and as the clock pulses, the data propagates through the flip-flops, ultimately appearing at the output.

The logic circuit provided below demonstrates a serial-in serial-out (SISO) shift register. It comprises four D flip-flops that are interconnected in a sequential manner. These flip-flops operate synchronously with one another, as they all receive the same clock signal.

![image](https://github.com/naavaneetha/SERIAL-IN-SERIAL-OUT-SHIFTREGISTER/assets/154305477/e81c4072-37f9-46c6-8145-566764b74c3a)

Figure 01 4 Bit SISO Register

The synchronous nature of the flip-flops ensures that the shifting of data occurs in a coordinated manner. When the clock signal rises, the input data is sampled and stored in the first flip-flop. On subsequent clock pulses, the stored data propagates through the flip-flops, moving from one flip-flop to the next.
Each D flip-flop in the circuit has a Data (D) input, a Clock (CLK) input, and an output (Q). The D input represents the data to be loaded into the flip-flop, while the CLK input is connected to the common clock signal. The output (Q) of each flip-flop is connected to the D input of the next flip-flop, forming a cascade.

**Procedure**

// 1. Create a Verilog module with inputs clock, reset, and serial_in, and output serial_out.

2. Use a register to store the shift register contents.

3. Apply an asynchronous reset to clear all flip-flops.

4. On every positive clock edge, shift the data by one position.

5. Insert the serial_in bit into the least significant bit.

6. Take the most significant bit as serial_out.

7. Compile and simulate the design in Quartus to verify the output. //

**PROGRAM**

/*
Developed by:Monisha D 
RegisterNumber:25007487
*/
```
module siso_shift_register (
    input clk,          // Clock input
    input reset,        // Asynchronous reset
    input serial_in,    // Serial data input
    output serial_out   // Serial data output
);

reg [3:0] q;            // Internal shift register

always @(posedge clk or posedge reset) begin
    if (reset)
        q <= 4'b0000;               // Clear register on reset
    else
        q <= {q[2:0], serial_in};   // Shift left, insert serial_in
end

assign serial_out = q[3];           // MSB is serial output

endmodule
```

**RTL LOGIC FOR SISO Shift Register**

![RTL for serial in serial out](https://github.com/user-attachments/assets/822c3190-8faa-40be-9ab2-1134d321ce67)


**TIMING DIGRAMS FOR SISO Shift Register**

![Waveform for serial in serial out ](https://github.com/user-attachments/assets/6453224d-2883-40c4-b286-379053c4b517)


**RESULTS**

Thus the Serial-In Serial-Out shift register is implemented and verified.
