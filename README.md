# JKFLIPFLOP-USING-IF-ELSE

**AIM:** 

To implement  JK flipflop using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**JK Flip-Flop**

JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.

![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/a649c30b-232b-4558-b188-fd6c09845180)


This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs. The following table shows the state table of JK flip-flop.

![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/c4360742-e8a8-4937-b089-c46c0433f9a3)

 
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop. Present Inputs Present State Next State
 
![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/6c275261-a6d5-4c37-a3a7-1e88ca11c4cd)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
 
![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/5174f41b-0ce0-4329-a372-6d1943ea6673)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

**Procedure**

/* write all the steps invloved */
```
1.Use module projname(input,output) to start the Verilog programming.
2.Assign inputs and outputs using the word input and output respectively.
3.Use defined keywords like wire,assign and required logic gates to represent the boolean expression.
4.Use each output to represent one for difference and the other for borrow.
5.End the verilog program using keyword endmodule
```

**PROGRAM**

/* Program for flipflops and verify its truth table in quartus using Verilog programming. Developed by:SHAABIN R S RegisterNumber:24006663
*/
```
module jk_flipflop (
    input wire clk,   // Clock signal
    input wire j,     // J input
    input wire k,     // K input
    input wire reset, // Asynchronous reset
    output reg q,     // Q output
    output wire q_bar // Complement of Q
);

    // Complement of Q
    assign q_bar = ~q;

    always @(posedge clk or posedge reset) begin
        if (reset) begin
            q <= 1'b0; // Reset Q to 0
        end else begin
            case ({j, k})
                2'b00: q <= q;          // No change
                2'b01: q <= 1'b0;       // Reset
                2'b10: q <= 1'b1;       // Set
                2'b11: q <= ~q;         // Toggle
                default: q <= q;        // Default case (redundant)
            endcase
        end
    end

endmodule
```

**RTL LOGIC FOR FLIPFLOPS**
![Screenshot 2024-12-29 212813](https://github.com/user-attachments/assets/0cf3c3ee-d314-4e04-b892-467318828627)


**TIMING DIGRAMS FOR FLIP FLOPS**
![Screenshot 2024-12-29 212835](https://github.com/user-attachments/assets/98a60b9e-0b67-43c7-9f99-d374a8d6513f)


**RESULTS**

Thus the JK flipflop is implemented using verilog and validated their functionality using their functional table
