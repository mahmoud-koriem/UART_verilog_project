Verilog UART Implementation
A robust and parameterizable UART (Universal Asynchronous Receiver-Transmitter) module implemented in Verilog, designed for easy integration into any FPGA project.

Author: MAHMOUD AHMED KORIEM
Date: September 13, 2025
1. About The Project
This project provides a complete Verilog implementation of a UART, a fundamental component for serial communication. The design is lightweight, fully synthesizable, and intended for easy portability across different FPGA platforms.

The implementation handles the serialization of parallel data for transmission and the de-serialization of incoming serial data for reception, complete with start, stop, and data bits.

Key Features
Parameterizable: Easily configure the system clock frequency and baud rate.

Standard Compliant: Follows the standard UART protocol (8-N-1 format: 8 data bits, no parity, 1 stop bit).

Modular Design: Separate, clean modules for the transmitter (uart_tx) and receiver (uart_rx).

Self-Checking Testbench: Includes a comprehensive testbench to verify correct functionality in a loopback configuration.

2. Repository Contents
File

Description

uart_tx.v

The transmitter module. Serializes and transmits an 8-bit data byte.

uart_rx.v

The receiver module. Receives and de-serializes an incoming data stream into an 8-bit byte.

uart.v

The top-level wrapper that integrates the TX and RX modules into a single, user-friendly interface.

uart_tb.v

A simulation testbench to validate the entire UART module.

3. Getting Started
Simulation
You can verify the design's functionality using any standard Verilog simulator (e.g., ModelSim, Vivado Simulator, Icarus Verilog).

Add all Verilog source files (.v) to your simulation project.

Set uart_tb as the top-level module for the simulation.

Run the simulation. The testbench will output success or failure messages to the console.

Integration
To use the UART in your own hardware design:

Instantiate the top-level uart module in your project.

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

4. Configuration
The module's behavior is controlled by two top-level parameters.

Parameter

Description

Default Value

CLK_FREQ

The frequency of the input system clock in Hertz.

50_000_000 (50MHz)

BAUD_RATE

The desired serial communication speed in bits/sec.

9600

This README was generated for the Verilog UART project by Mahmoud Ahmed Koriem.
