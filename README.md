# DFS Pulse Tester

Dynamic Frequency Selection (DFS) is a mechanism that allows a radio device to dynamically select or change the operating frequency to avoid interfering with other systems, such as local weather radar systems. This GNU Radio Companion (GRC) flow graph **emulates radar signal patterns for DFS testing** using a suitable Software Defined Radio (SDR), such as the HackRF One. You can select the center frequency and type of radar signature.

![DFS Pulse Tester](../master/dfs_pulse_tester.png "DFS Pulse Tester")

For more information on DFS in the context of Wi-Fi networks see [A Practical Introduction to Dynamic Frequency Selection](https://www.adriangranados.com/blog/practical-intro-dfs).

## Instructions

Follow these steps to automatically setup and provision an Ubuntu virtual machine (VM) with the necessary software and libraries to run the flow graph with your HackRF. If you already have an environment setup to use your HackRF, you can skip to step 5.

1. Install [Vagrant](https://www.vagrantup.com/downloads.html), [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and the [VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads) (required to enable USB support in VirtualBox). If you have any of these components already installed, please make sure you're running the latest version.
2. Setup and provision the VM automatically using Vagrant:
```bash
git clone https://github.com/adriangranados/dfs-pulse-tester.git
cd dfs-pulse-tester
vagrant plugin install vagrant-vbguest
vagrant up
vagrant reload
```
3. Plug in the HackRF and attach it to the VM by clicking the USB icon in the bottom right of the VirtualBox VM window and choosing *Great Scott Gadgets HackRF ONE*.
4. Login to the VM (choose the *hackrf* user and enter password *hackrf*).
5. Launch the GRC (GNU Radio Companion) application and open the *dfs_pulse_tester.grc* file (if you're using the VM provisioned using the steps above, the file will be located in */home/hackrf/*).
6. Play the flow graph, then select the channel, radar signature and start the pulse (*Pulse > Start*).

## Authors

* Adrian Granados - [@adriangranados](https://twitter.com/adriangranados)
* Nigel Bowden - [@wifinigel](https://twitter.com/wifinigel)

## Disclaimer

*This flow graph is provided for testing purposes only. Check local and federal regulations and obtain permission before using.*
