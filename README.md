# full_adder-8-bit
module full_adder_8bit(
    input [7:0] a,
    input [7:0] b,
    input cin,
    output [7:0] sum,
    output cout
);

wire [8:0] carry; // เปลี่ยนจาก [7:0] เป็น [8:0]

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

module full_adder(
    input a,
    input b,
    input cin,
    output sum,
    output cout
);

assign {cout, sum} = a + b + cin;

endmodule
