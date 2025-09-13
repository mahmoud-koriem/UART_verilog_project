# UART_verilog_project
A simple UART transmitter and receiver implemented in Verilog
Author: MAHMOUD AHMED KORIEM
Date: September 13, 2025

1. About The Project
This project is a complete implementation of a Universal Asynchronous Receiver-Transmitter (UART) module in the Verilog HDL. The design is intended to be simple, parameterizable, and easily portable to any FPGA platform.

The UART protocol is a standard for serial communication, allowing for the transmission of data between two devices one bit at a time. This implementation includes:

A Transmitter (TX) to serialize parallel data.

A Receiver (RX) to de-serialize incoming serial data.

A top-level wrapper for easy integration.

A self-checking testbench to verify functionality.

2. File Structure
The repository contains the following Verilog source files:

uart_tx.v: The UART transmitter module. It takes an 8-bit parallel byte and transmits it serially, adding the necessary start and stop bits.

uart_rx.v: The UART receiver module. It samples the incoming serial line, detects the start bit, reads the data bits, and outputs the 8-bit parallel byte.

uart.v: The top-level UART module that instantiates and connects the transmitter and receiver. This file provides a clean interface for the user's design.

uart_tb.v: A testbench designed to simulate and verify the functionality of the top-level uart module in a loopback configuration.

3. How to Use
Simulation
To verify the design, you can run a simulation using any standard Verilog simulator (like ModelSim, Vivado Simulator, Icarus Verilog, etc.).

Compile all the Verilog files (uart.v, uart_tx.v, uart_rx.v, uart_tb.v).

Set uart_tb as the top-level simulation module.

Run the simulation. The testbench will automatically send a byte of data ('A') and then a second byte ('Z'), and it will report in the console whether the received byte matches the transmitted one.

Integration
To integrate the UART into your own project:

Instantiate the uart module from uart.v.

Configure the CLK_FREQ and BAUD_RATE parameters to match your system's clock frequency and desired communication speed.

Example Instantiation:

uart #(
    .CLK_FREQ(50_000_000), // 50 MHz system clock
    .BAUD_RATE(9600)      // 9600 baud rate
) my_uart_instance (
    .i_Clk(my_system_clock),
    .i_Rx(uart_rx_pin),
    .o_Tx(uart_tx_pin),
    // Connect other ports to your logic
    // ...
);

4. Module Parameters
The top-level uart.v module can be configured with the following parameters:

CLK_FREQ: The frequency of the input system clock (i_Clk) in Hertz.

Default: 50_000_000 (50 MHz)

BAUD_RATE: The desired communication speed in bits per second.

Default: 9600

The module automatically calculates the required clock-per-bit value to achieve the specified baud rate.

This README was generated for the Verilog UART project by Mahmoud Ahmed Koriem.
