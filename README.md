# VHDL Counter Bug

This repository demonstrates a common, yet subtle, bug in VHDL code: an off-by-one error in a counter and a process missing a signal in the sensitivity list.  The `bug.vhdl` file contains the buggy code. The solution addresses both issues. 

## Bug Description

The `buggy_counter` entity is intended to count from 0 to 15, resetting to 0 when it reaches 15. However, under certain circumstances, the counter might not reset correctly or behave unexpectedly.  Additionally, the sensitivity list of the process only includes `clk` and `rst`. Adding `internal_count` will fix a potential issue caused by the implicit sensitivity on all signals within a process.

## Solution

The `bugSolution.vhdl` file provides a corrected version of the counter that addresses both issues:
1. It explicitly handles the case where the counter reaches 15 for correct reset.
2. It includes `internal_count` in the process sensitivity list, addressing a race condition and ensuring that assignments to `internal_count` correctly trigger the process.
