# Wireless_ESTOP
Wireless ESTOP that works with BEAR actuators

This repo currently contains the open-source code for the transmitter and receiver of the Lite version of our Wireless ESTOP system, which uses RP2040 as its MCU and NRF24 for 2.4GHz wireless communication.

## Licensing
The Wireless ESTOP is dual-licensed under both commercial and open-source licenses. The work in this repo is under GNU General Public License (GPL) version 3, which is ideal for use cases such as open-source projects with open-source distribution, student/academic purposes, hobby projects, internal research projects without external distribution, or other projects where all GPL obligations can be met. Read the full text of [the GNU GPL version 3](https://www.gnu.org/licenses/gpl-3.0.html) for details.  
Contact us for commercial license should you need full rights to create and distribute the platform on your own terms without any open-source license obligations.

## Building with Arduino CLI

The sketches are intended for the Raspberry Pi Pico family. They can be built
either in the Arduino IDE or from the command line using
[**arduino-cli**](https://github.com/arduino/arduino-cli). The steps below show
how to compile the receiver firmware from a terminal:

1. Install `arduino-cli` (see the project page for install script).
2. Add the RP2040 board package:

   ```bash
   arduino-cli config init
   arduino-cli config add board_manager.additional_urls \
     https://github.com/earlephilhower/arduino-pico/releases/download/4.6.0/package_rp2040_index.json
   arduino-cli core update-index
   arduino-cli core install rp2040:rp2040
   ```

3. Compile the sketch:

   ```bash
   arduino-cli compile --fqbn rp2040:rp2040:rpipico ESTOP_Lite/Rev0/RX
   ```

You can replace `RX` with `TX` to build the transmitter firmware. The compiled
`*.uf2` file will be placed in the `build` directory and can be flashed to a
Pico board via USB bootloader mode.

## Serial Monitoring

The receiver outputs a single status byte over USB serial whenever its state
changes. The bits are defined as:

- bit 0 – STOP pressed
- bit 1 – soft stop pressed
- bit 2 – communication error

A host (for example a ROS 2 node) can listen to this byte stream to react to
state changes with minimal latency.

## Buttons and Pinout on Receiver 
<img src="https://github.com/Westwood-Robotics/Wireless_ESTOP/blob/main/ESTOP_Lite/Rev0/Pic/FRONT.jpg" width=50% height=50%>
<img src="https://github.com/Westwood-Robotics/Wireless_ESTOP/blob/main/ESTOP_Lite/Rev0/Pic/ISO.jpg" width=60%>

## 3D Model
RX Module(Receiver): https://github.com/Westwood-Robotics/Wireless_ESTOP/blob/main/ESTOP_Lite/Rev0/Dummy/ESTOP_RX.STEP



# estop_firmware
