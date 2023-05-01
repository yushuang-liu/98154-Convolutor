# 98154 - Convolutor Tape Out

Yushuang Liu
98154 Spring 2023 Final Tapeout Project

## Overview

This device takes in two 6-bit inputs and returns their convolution result. To accomodate chip manufacturing requirements, the two inputs are combined into one 12-bit input io_in.

## How it Works

The input signals are passed into shift registers to get the LSB's on every rising clock edge. The LSB's are then input into a one-bit multiplier (implemented simply as anding). An adder sums together all the products. One of the inputs is the new product, and the other is either the existing sum or zero, selected by a Mux. The final output is stored to a register. All devices are controlled by an FSM with 8 states.

Here are the RTL and FSM for the design:

![](RTL Final.jpg)
![](FSM Final.jpg)

## Inputs/Outputs

Despite the designated pins used for clock and reset, the 12-bit input is divided into even halves to create two inputs for the convolution. The output is the lower 4 bits of the 12 pins.

## Hardware Peripherals

No additional hardware peripherals is used.

## Design Testing / Bringup

The design is tested with a testbench written in SystemVerilog. Test input is 12'b110111110101, test output is 4'b0100, as desired.

## Media

For full SystemVerilog code for the design and testbench, please go to EDAPlayground at the following link:
https://edaplayground.com/x/CgaV