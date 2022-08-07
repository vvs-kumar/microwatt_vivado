# microwatt_vivado
Implementing Microwatt soc minimal from varunmadhavam github page and tweeking it the codes. 

Download files from github page 
https://github.com/varunmadhavam/microwatt-soc-minimal.git

Opening the project file in vivdo EITHER In Ubuntu or Windows.

In Ubuntu we have to install driver for Uploading to boards manually by running -
./install_drivers

In the following path-

<Vivado Install Path>/data/xicom/cable_drivers/lin64/install_script/install_drivers/

Open vivado(2021.2) and open Varunmadhavam github page's project file.

Editing the file "top-arty.vhdl" from line number - 128
  
From this lines of codes:
    gpio_in(0) <= sw(0);
    gpio_in(1) <= sw(1);
    gpio_in(2) <= sw(2);
    gpio_in(3) <= sw(3);

    led(0) <= gpio_out(0) when gpio_dir(0) = '1' else 'Z';
    led(1) <= gpio_out(1) when gpio_dir(1) = '1' else 'Z';
    led(2) <= gpio_out(2) when gpio_dir(2) = '1' else 'Z';
    led(3) <= gpio_out(3) when gpio_dir(3) = '1' else 'Z';
  
  To 
    led(0) <= sw(0);
    led(1) <= sw(1);
    led(2) <= sw(2):
    led(3) <= sw(3); 

The above code is for swith led control in arty A7 100t.

Run Synthesis, Implementation and Dump the code to board. 
