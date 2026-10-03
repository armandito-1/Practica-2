# PROBLEMA 1
<img width="888" height="813" alt="{BA670F2A-D222-44DB-89AC-C79D431A8DF7}" src="https://github.com/user-attachments/assets/6eae7c29-c3d5-4aab-95bf-33f736d2da4c" />

# PROBLEMA 2
<img width="849" height="483" alt="{B929B4C7-F325-4629-90EF-B67ED70CC23A}" src="https://github.com/user-attachments/assets/95ebf0ab-cedc-4edd-afba-22be1645ceda" />
<img width="839" height="324" alt="{FB8B73D2-FBCE-4071-BA25-340C5C3BA71E}" src="https://github.com/user-attachments/assets/6dbac629-d1a6-41bb-a9a5-10d053c7b3b1" />

# PROBLEMA 3
<img width="831" height="776" alt="{3D1EC905-5DCF-410F-B51F-8FBD30BB7FA6}" src="https://github.com/user-attachments/assets/6961134a-6e20-4bb6-909a-375b7dfc15ee" />

# PROBLEMA 4
<img width="839" height="299" alt="{EE43BB92-CB7F-4BEB-B9D3-EE5848EA6C67}" src="https://github.com/user-attachments/assets/b4deb723-3af5-4652-b07a-4f45c95dfc5a" />

# PROBLEMA 5
<img width="859" height="384" alt="{22230A59-9767-410B-AF01-43BA6CC677C8}" src="https://github.com/user-attachments/assets/8b5503f9-8e14-4536-a4b7-0b07b3e7af57" />
<img width="851" height="579" alt="{2F7F4059-F88F-42F9-B2A2-12674C3EFC04}" src="https://github.com/user-attachments/assets/42657cae-5e52-412e-b30e-f159a2b63703" />

# PROBLEMA 6
<img width="878" height="371" alt="{4C402B20-4A08-4238-96B2-B25CFE6A2CA7}" src="https://github.com/user-attachments/assets/ce89c6e6-5d57-46d5-a3d0-3b17ed8c3c60" />

# PROBLEMA 7
<img width="891" height="360" alt="{8241F14A-3B31-4EBA-BCCA-3CA2BEFDC9E8}" src="https://github.com/user-attachments/assets/070c2c20-8100-429c-8f1c-1152a8076974" />

# PROBLEMA 8
<img width="919" height="767" alt="{18F14844-1CD7-46FC-BAE2-F394754D0947}" src="https://github.com/user-attachments/assets/3b753149-dbec-4cf7-9fa6-e6a03f760076" />

# PROBLEMA 9
<img width="897" height="421" alt="{4A722311-3FD2-4FC5-9C45-4736665CAFC6}" src="https://github.com/user-attachments/assets/d5e755b2-ef0d-42a6-a84a-1084addc0933" />

# PROBLEMA 10
<img width="928" height="504" alt="{AA9C54B7-8134-4EDD-9917-66F85175CE20}" src="https://github.com/user-attachments/assets/41ad88cd-ec41-43f6-9104-cce79e45a3b8" />

# PROBLEMA 11

<img width="1920" height="1017" alt="{B1B80A06-015E-4432-86AD-B1DF107A17E2}" src="https://github.com/user-attachments/assets/8c78fb0c-d57f-4224-890e-bcaa769b73ae" />
<img width="1600" height="694" alt="image" src="https://github.com/user-attachments/assets/5584548c-d481-4fdd-bdcf-9e6f70ccb8f2" />

## codigo de verilog
//MACRO MÓDULO (jerarquía DESCENDENTE)
module hernesto(iSelect,oDisplay1,oDisplay2,oDisplay3,
 oDisplay4,oDisplay5,oDisplay6);
input [2:0] iSelect;
output [6:0] oDisplay1,oDisplay2,oDisplay3,oDisplay4,oDisplay5,oDisplay6;
wire [3:0] dato1, dato2, dato3, dato4, dato5, dato6;
wire [5:0] display_n;
wire [3:0] iA = 4'b0001;
mydeco3to6 IC01(display_n,iSelect); //mydeco3to6(Y,D)
mymux4to4 IC02(dato1,iA,display_n[0]); //mymux4to4(Y,A,S)
mymux4to4 IC03(dato2,iA,display_n[1]);
mymux4to4 IC04(dato3,iA,display_n[2]);
mymux4to4 IC05(dato4,iA,display_n[3]);
mymux4to4 IC06(dato5,iA,display_n[4]);
mymux4to4 IC07(dato6,iA,display_n[5]);
mydeco_display7 IC08(oDisplay1,dato1); //mydeco_display7(Seg,A)
mydeco_display7 IC09(oDisplay2,dato2);
mydeco_display7 IC10(oDisplay3,dato3);
mydeco_display7 IC11(oDisplay4,dato4);
mydeco_display7 IC12(oDisplay5,dato5);
mydeco_display7 IC13(oDisplay6,dato6);
endmodule
//Submódulo: DECODIFICADOR binario a 7 seg. (Modelado de comportamiento)
module mydeco_display7(Seg,A);
input [3:0] A;
output reg [6:0] Seg; //Seg[6]=a, Seg[5]=b, ... , Seg[1]=f, Seg[0]=g
always @*
case (A) 
	4'b0000 : Seg <= 7'b0000001; //Hexadecimal 0 (0000001)
	4'b0001 : Seg <= 7'b1111001; //Hexadecimal 1 (1001111)
	4'b0010 : Seg <= 7'b0100100; //Hexadecimal 2 (0010010)
	4'b0011 : Seg <= 7'b0110000; //Hexadecimal 3 (0000110)
	4'b0100 : Seg <= 7'b0011001; //Hexadecimal 4 (1001100)
	4'b0101 : Seg <= 7'b0010010; //Hexadecimal 5 (0100100)
	4'b0110 : Seg <= 7'b0000010; //Hexadecimal 6 (0100000)
	4'b0111 : Seg <= 7'b1111000; //Hexadecimal 7 (0001111)
	4'b1000 : Seg <= 7'b0000000; //Hexadecimal 8 (0000000)
	4'b1001 : Seg <= 7'b0011000; //Hexadecimal 9 (0001100)
	4'b1010 : Seg <= 7'b0001000; //Hexadecimal A (0001000)
default : Seg <= 7'b1111111; //Apaga el display (1111111)
endcase

endmodule

//Submódulo: MULTIPLEXOR 4 a 4 (Modelado de flujo de datos)
module mymux4to4(Y,A,S);
input [3:0] A;
input S;

output [3:0] Y;

assign Y = S ? A : 4'b1111;

endmodule

//Submódulo: DECODIFICADOR 3 a 6 (Modelado de nivel de compuertas)
module mydeco3to6(Y,D);
input [2:0] D;
output [5:0] Y;

wire A, B, C;
wire Anot, Bnot, Cnot;

buf (A,D[0]);
buf (B,D[1]);
buf (C,D[2]);

not (Anot,D[0]);
not (Bnot,D[1]);
not (Cnot,D[2]);

and g1(Y[0],Cnot,Bnot,A); //001
and g2(Y[1],Cnot,B,Anot); //010
and g3(Y[2],Cnot,B,A); //011
and g4(Y[3],C,Bnot,Anot); //100
and g5(Y[4],C,Bnot,A); //101
and g6(Y[5],C,B,Anot); //110

endmodule

# PROBLEMA 12

# PROBLEMA 13
