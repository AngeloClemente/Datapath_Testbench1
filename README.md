# Datapath_Testbench1
module NewDatapath_Testbench();

// inputs
	reg clock;
	reg reset;
	
// wires 
	wire [63:0] X1, X3, X7, X9, X12, X23; // Registers
	wire [63:0] M1, M0, M50; // Memory
	wire [63:0] PC;

	assign X1 = dut.regfile.R01;
	assign X3 = dut.regfile.R03;
	assign X7 = dut.regfile.R07;
	assign X9 = dut.regfile.R09;
	assign X12 = dut.regfile.R12;
	assign M1 = dut.data_mem.mem[1];
	assign M50 = dut.data_mem.mem[50];
	assign M0 = dut.data_mem.mem[0];
	assign X23 = dut.regfile.R23;
	assign PC = dut.PC.PC;
	
	DatapathLEGv8 dut (clock, reset);
	
	initial begin
		reset = 1'b1;
		clock = 1'b0;
		
		#9 reset = 1'b0;
		
		#5000 $stop; 
	end
	
	always begin
		#100 clock = ~clock;
	end

endmodule 
