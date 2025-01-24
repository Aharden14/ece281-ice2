# ICE 2: Half-Adder

Code for [ECE 281 ICE 2: Half-Adder](https://usafa-ece.github.io/ece281-book/ICE/ICE2.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Windows 11 using Vivado 2024.

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

First, the workflow uses GHDL to **analyze** all `.vhd` files in `src/hdl/`.

Then it **elaborates** the *any* entity with the name `*_tb`. In this case, that is `helloled_tb`.

Finally, the workflow **runs** the simulation. If successful then it will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity failure` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels will be reported, but not fail the workflow.

![image](https://github.com/user-attachments/assets/ec379f12-8d7b-44ce-ae5b-36e9704a8f9a)
![image](https://github.com/user-attachments/assets/267ad2ee-719f-4290-810f-2d84321d2ee0)
![image](https://github.com/user-attachments/assets/046b3220-297a-499d-8eb3-b087d90019c7)
![image](https://github.com/user-attachments/assets/8af571fe-dc3b-45d7-9206-abd2539cd18d)

Documentation: I looked up how to commit files from git bash
