Verilog UART Implementation
A robust and parameterizable UART (Universal Asynchronous Receiver-Transmitter) module implemented in Verilog, designed for easy integration into any FPGA project.

Author: MAHMOUD AHMED KORIEM
1. About The Project
This project provides a complete Verilog implementation of a UART, a fundamental component for serial communication. The design is lightweight, fully synthesizable, and intended for easy portability across different FPGA platforms.

The implementation handles the serialization of parallel data for transmission and the de-serialization of incoming serial data for reception, complete with start, stop, and data bits.

2. Project Structure
.
├── README.md
├── scrs/
│   ├── uart.v
│   ├── uart_rx.v
│   └── uart_tx.v
└── tb/
    └── uart_tb.v

Folder/File
Description
scrs/Contains all the synthesizable source code for the UART module.

tb/Contains the simulation testbench used to verify the design.

3. Getting Started
Simulation
You can verify the design's functionality using any standard Verilog simulator (e.g., ModelSim, Vivado Simulator, Icarus Verilog).

Add the Verilog source files from the scrs/ directory.

Add the testbench file from the tb/ directory.

Set uart_tb as the top-level module for the simulation.

Run the simulation. The testbench will output success or failure messages to the console.

Integration
To use the UART in your own hardware design:

Instantiate the top-level uart module from scrs/uart.v in your project.

Set the CLK_FREQ and BAUD_RATE parameters to match your system's requirements.

Example Instantiation:

uart #(
    .CLK_FREQ(50_000_000), // 50 MHz system clock
    .BAUD_RATE(9600)      // 9600 baud rate
) my_uart_instance (
    .i_Clk(my_system_clock),
    .i_Rx(uart_rx_pin),
    .o_Tx(uart_tx_pin),
    
    // Connect data signals to your application logic
    .i_Tx_DV(tx_data_valid),
    .i_Tx_Byte(tx_byte_out),
    .o_Rx_DV(rx_data_valid),
    .o_Rx_Byte(rx_byte_in)
);

