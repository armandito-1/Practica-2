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
## presentado en clase

# PROBLEMA 12
<img width="1346" height="688" alt="{C118DF7B-1F1F-47E1-BA5C-2B112AD0B1AC}" src="https://github.com/user-attachments/assets/5d1c89c0-eab9-45ca-84ca-82cd86bbdae1" />
<img width="1621" height="969" alt="{7313D213-7910-4013-9214-AD7BDF5130F1}" src="https://github.com/user-attachments/assets/1c266310-535b-4665-9f7d-4aa1e71db385" />
<img width="1920" height="1018" alt="{7FB9A880-3613-4900-BBF0-6660BD50812F}" src="https://github.com/user-attachments/assets/de4148f2-db7f-40a6-a5ed-229ac9a29319" />

## codifo de verilog
module bcd_gray_display (
    input      [3:0] BCD,
    output     [3:0] LED_GRAY,
    output           ERROR,
    output reg [6:0] HEX4,
    output reg [6:0] HEX5
);

    /*
     * La entrada es invalida cuando el valor binario
     * ingresado es mayor que 9.
     */
    assign ERROR = (BCD > 4'd9);

    /*
     * Conversion de binario/BCD a codigo Gray.
     */
    assign LED_GRAY[3] = BCD[3];
    assign LED_GRAY[2] = BCD[3] ^ BCD[2];
    assign LED_GRAY[1] = BCD[2] ^ BCD[1];
    assign LED_GRAY[0] = BCD[1] ^ BCD[0];

    /*
     * Decodificador BCD a 7 segmentos.
     *
     * HEX4: quinto display fisico, muestra el numero.
     * HEX5: sexto display fisico, muestra la letra E.
     *
     * Los displays de la DE0-CV son activos en bajo:
     * 0 = segmento encendido
     * 1 = segmento apagado
     *
     * Orden de los bits:
     * HEX[6:0] = {g, f, e, d, c, b, a}
     */
    always @(*) begin

        /*
         * Valores predeterminados:
         * ambos displays apagados.
         */
        HEX4 = 7'b1111111;
        HEX5 = 7'b1111111;

        if (ERROR == 1'b1) begin

            /*
             * Entrada invalida: valores entre 10 y 15.
             *
             * HEX4 queda apagado.
             * HEX5 muestra la letra E.
             */
            HEX4 = 7'b1111111;
            HEX5 = 7'b0000110;

        end
        else begin

            /*
             * Entrada valida: valores entre 0 y 9.
             *
             * HEX5 queda apagado.
             * HEX4 muestra el numero ingresado.
             */
            HEX5 = 7'b1111111;

            case (BCD)

                4'd0: HEX4 = 7'b1000000; // Numero 0
                4'd1: HEX4 = 7'b1111001; // Numero 1
                4'd2: HEX4 = 7'b0100100; // Numero 2
                4'd3: HEX4 = 7'b0110000; // Numero 3
                4'd4: HEX4 = 7'b0011001; // Numero 4
                4'd5: HEX4 = 7'b0010010; // Numero 5
                4'd6: HEX4 = 7'b0000010; // Numero 6
                4'd7: HEX4 = 7'b1111000; // Numero 7
                4'd8: HEX4 = 7'b0000000; // Numero 8
                4'd9: HEX4 = 7'b0010000; // Numero 9

                default: HEX4 = 7'b1111111;

            endcase

        end

    end

endmodule
## presentado en clase

# PROBLEMA 13
<img width="1920" height="1017" alt="{97AC6D98-C5A8-4729-8708-F100CE49BF59}" src="https://github.com/user-attachments/assets/1d760a52-c53f-4710-9d46-cfe98e77e562" />
<img width="1920" height="1014" alt="{6D2B5F7C-74DB-45D4-B0AC-497A36487F80}" src="https://github.com/user-attachments/assets/277d7443-340f-4be4-beeb-2cabae0d9c98" />

## codigo de verilog
module PedroPascal(

    // =========================================
    // ENTRADAS
    // =========================================

    input wire [4:0] A,
    input wire [4:0] B,

    // OP corresponde a los cuatro botones KEY
    input wire [3:0] OP,

    // =========================================
    // SALIDAS
    // =========================================

    output wire [4:0] F,
    output wire COUT,

    output wire [6:0] HEX0,
    output wire [6:0] HEX1

);

    // =========================================
    // VARIABLES INTERNAS
    // =========================================

    reg [4:0] resultado;
    reg carry;

    // Los botones de la DE0-CV son activos en bajo.
    // Por eso invertimos OP.
    wire [3:0] OP_REAL;

    assign OP_REAL = ~OP;


    // =========================================
    // UNIDAD ARITMETICO LOGICA
    // =========================================

    always @(*) begin

        // Valores por defecto
        resultado = 5'b00000;
        carry = 1'b0;

        case (OP_REAL)

            // =====================================
            // INSTRUCCION 0
            // F = A
            // =====================================

            4'h0: begin

                resultado = A;
                carry = 1'b0;

            end


            // =====================================
            // INSTRUCCION 1
            // F = A + 1
            // =====================================

            4'h1: begin

                {carry, resultado} =
                    {1'b0, A} + 6'b000001;

            end


            // =====================================
            // INSTRUCCION 5
            // F = A + B' + 1
            // =====================================

            4'h5: begin

                {carry, resultado} =
                    {1'b0, A} +
                    {1'b0, ~B} +
                    6'b000001;

            end


            // =====================================
            // INSTRUCCION B
            // F = A OR B
            // =====================================

            4'hB: begin

                resultado = A | B;
                carry = 1'b0;

            end


            // =====================================
            // INSTRUCCION D
            // F = (A > B)
            // =====================================

            4'hD: begin

                if (A > B)
                    resultado = 5'b00001;
                else
                    resultado = 5'b00000;

                carry = 1'b0;

            end


            // =====================================
            // CUALQUIER OTRA INSTRUCCION
            // =====================================

            default: begin

                resultado = 5'b00000;
                carry = 1'b0;

            end

        endcase

    end


    // =========================================
    // CONEXION DE LAS SALIDAS
    // =========================================

    assign F = resultado;

    assign COUT = carry;


    // =========================================
    // DISPLAY HEX0
    // MUESTRA LOS 4 BITS INFERIORES
    // =========================================

    HEX7SEG DISPLAY0 (

        .HEX(resultado[3:0]),
        .SEG(HEX0)

    );


    // =========================================
    // DISPLAY HEX1
    // MUESTRA EL BIT 4
    // =========================================

    HEX7SEG DISPLAY1 (

        .HEX({3'b000, resultado[4]}),
        .SEG(HEX1)

    );

endmodule



// ========================================================
// DECODIFICADOR PARA DISPLAY DE 7 SEGMENTOS
// ========================================================

module HEX7SEG (

    input wire [3:0] HEX,
    output reg [6:0] SEG

);

    always @(*) begin

        case (HEX)

            4'h0: SEG = 7'b1000000;
            4'h1: SEG = 7'b1111001;
            4'h2: SEG = 7'b0100100;
            4'h3: SEG = 7'b0110000;
            4'h4: SEG = 7'b0011001;
            4'h5: SEG = 7'b0010010;
            4'h6: SEG = 7'b0000010;
            4'h7: SEG = 7'b1111000;
            4'h8: SEG = 7'b0000000;
            4'h9: SEG = 7'b0010000;

            4'hA: SEG = 7'b0001000;
            4'hB: SEG = 7'b0000011;
            4'hC: SEG = 7'b1000110;
            4'hD: SEG = 7'b0100001;
            4'hE: SEG = 7'b0000110;
            4'hF: SEG = 7'b0001110;

            default:
                SEG = 7'b1111111;

        endcase

    end

endmodule
