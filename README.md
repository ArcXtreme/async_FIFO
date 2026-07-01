# Asynchronous dual clock FIFO

# Overview

This repository stores a verilog description of dual clock FIFO. A FIFO is
a convenient circuit to exchange data between two clock domains. It manages
the RAM addressing internally, the clock domain crossing and informs the user
of the FIFO fillness with "full" and "empty" flags.

It is widely inspired by the excellent article from Clifford Cummings,
[Simulation and Synthesis Techniques for Asynchronous FIFO
Design](http://www.sunburst-design.com/papers/CummingsSNUG2002SJ_FIFO1.pdf).

The simulation testcases available use [Icarus Verilog](http://iverilog.icarus.com) and SVUT tool to run the tests.

The FIFO is fully functional and used in many successful projects.

# Usage

RTL sources are present in RTL folder under three flavors:
- `rtl/async_fifo.v`: a basic asynchronous dual-clock FIFO
- `rtl/async_bidir_fifo.v`: two instance of the first one into a single top level for full-duplex channel
- `rtl/async_bidir_ramif_fifo.v`: same than previous but with external RAM

The three FIFOs have a list file to get the associated fileset.

The testbench in `sim/` provides an example about the instance and the configuration.

All three top levels have the same parameters:
- `DSIZE`: the size in bits of the datapath
- `ASIZE`: the size in bits of the internal RAM address bus. This implies the FIFO can be configured only with power of 2 depth
- `FALLTHROUGH`: allow to reduce the inner latency and propagate faster the data through the FIFO


