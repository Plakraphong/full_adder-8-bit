# full_adder-8-bit

`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    12:22:54 01/22/2024 
// Design Name: 
// Module Name:    full_adder_8bit 
// Project Name: 
// Target Devices: 
// Tool versions: 
// Description: 
//
// Dependencies: 
//
// Revision: 
// Revision 0.01 - File Created
// Additional Comments: 
//
//////////////////////////////////////////////////////////////////////////////////
module full_adder_8bit(
    input [7:0] a,
    input [7:0] b,
    input cin,
    output cout,
    output [7:0] sum
    );
wire [8:0] carry;
wire [7:0] sum_intermediate;

// เป็นการสร้าง Full Adder 8 บิตโดยการใช้การต่อเข้ามาของ Full Adder 1 บิต 8 ตัว
genvar i;
generate
    for (i = 0; i < 8; i = i + 1) begin
        full_adder fa(
            .a(a[i]),
            .b(b[i]),
            .cin(carry[i]),
            .sum(sum_intermediate[i]),
            .cout(carry[i+1])
        );
    end
endgenerate
assign sum = sum_intermediate;
assign cout = carry[8]; // carry out จะอยู่ที่ carry[8]

endmodule




`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    12:19:15 01/22/2024 
// Design Name: 
// Module Name:    full_adder 
// Project Name: 
// Target Devices: 
// Tool versions: 
// Description: 
//
// Dependencies: 
//
// Revision: 
// Revision 0.01 - File Created
// Additional Comments: 
//
//////////////////////////////////////////////////////////////////////////////////
module full_adder(
    input a,
    input b,
    input cin,
    output sum,
    output cout
);

assign {cout, sum} = a + b + cin;

endmodule


