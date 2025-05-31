## lab5

# mux_4to1_8bit.v

module mux_4to1_8bit(
    input [7:0] D0, D1, D2, D3, // 8-бітні інформаційні входи
    input A0, A1,               // Адресні входи
    output [7:0] Q              // 8-бітний вихід
);
    assign Q = (~A1 & ~A0) ? D0 :
               (~A1 & A0)  ? D1 :
               (A1 & ~A0)  ? D2 :
               (A1 & A0)   ? D3 : 8'b0;
endmodule


# mux_test.do

force D0 8'hA0 0ns  # 1010 0000
force D1 8'hB1 0ns  # 1011 0001
force D2 8'hC2 0ns  # 1100 0010
force D3 8'hD3 0ns  # 1101 0011
force A1 2'b0 0ns, 2'b1 40ns
force A0 2'b0 0ns, 2'b1 20ns, 2'b0 40ns, 2'b1 60ns
