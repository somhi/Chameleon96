# Presets for Chameleon96 board

See below how to load the presets into Platform Designer (Qsys).

This folder contains the following preset configuration files:

* DDR3_c96_Preset_1.qprs
  * It contains the memory presets for the Chameleon96 board



Load preset settings for Chameleon96 board (Qsys)
--------------------------------------------------------

Follow these steps from a file explorer:

* Browse to the Quartus project folder
* If not already present, create a new folder named "ip" and inside it another folder named "presets"
* Copy the presets file inside the [/ip/presets/](file:///ip/presets) folder. This file contains the preset settings for the Chameleon96 board.

If Qsys is still open, close it.  
From Quartus open the platform designer file: File > Open > select "soc_hps.qsys" (replace it with your own name) > Open

* Select View menu > Presets
* Select the preset file from the Project tree and press "Apply" button
* Close the presets window
* Click Generate HDL button at bottom page > Generate > Close  
* Click Finish to close Qsys.