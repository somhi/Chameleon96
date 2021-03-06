# Quartus & Qsys Project templates 

See below how to adapt the templates to your own project.

This folder contain the following project template:

* T01.basic-v1

  * main.bdf. Top block diagram containing:

    * Soc_hps block generated by Qsys
    * LoanIO control block
    * Simple counter block 
    * Debouncer block

  * soc_hps.qsys. Platform editor (Qsys) minimal project containing:

    * Cyclone V hard processor system, configured as:

      * Peripheral Pins: enabled SD and UART0
        * Mux table: 16 LoanIOs enabled (14,17,19,22,23,25,27,28,29,30,32,33,34,48,53,54)
      * HPS Clocks: enabled HPS-to-FPGA user 0 clock (100 MHz)
      * SDRAM chameleon96 presets loaded

    * Clock bridge

      


Adapt template for your own project
--------------------------------------------------------

Follow these steps:

* Download project template, decompress it, and rename folder as per your convenience.
* Open project file main.qpf
* In project navigator double click on main top object to open it
* Remove from block diagram everything you don't need like debouncer, counter, Wifi & BT led connections.
* Menu Project > Add/Remove files in project  > ...  > select and remove all that you removed in previous step
* Insert your own project module block (see below how to create blocks from HDL files)
* Connect clock `clk` signal to your module input clock
* All outputs from your modules that are defined as LoanIO's should go as inputs to the loanio_control block.
* All inputs to your modules that are defined as LoanIO's should come from loanio_in[xx] signals and shall be defined inside loanio_control block as inputs.
* Double click on loanio_control block and modify IO ports and adjust loanIOs as per your convenience.



If needed different soc_hps configuration:

* Open soc_hps.qsys in Platform editor (Qsys) and adapt it to your convenience.
* After that go to block editor in quartus and right click on the soc_hps block and update block.
* If you generated new pins on the soc_hps block, right click on the soc_hps block and click Generate pins for symbol ports.
* You would need surely to generate a new preloader so the changed configuration gets loaded when board boots (see tutorial section).

When all is done, just compile your project.

**Create blocks from Verilog modules**

* Open your Verilog file (File > Open > select file and check add file to current project)
* Alternatively create a new Verilog file  (File > New > Verilog HDL File > Ok)
* Create the block (File > Create/Update > Create Symbol Files for Current File)
* Insert the block into main block diagram



Program FPGA
--------------------------------------------------------

* Open the programmer (Tools menu > Programmer)
* Hardware Setup... > Hardware Settings > Double click "Arrow 96 CV SoC Board" > Close
* Add Device... > Soc Series V > double click SOCVHPS > Ok
* Select the "SOCVHPS" and press "Up" button
* Press the "Start" button to flash your core