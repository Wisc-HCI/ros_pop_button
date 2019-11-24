# ros_pop_button

Forked version of [brokeh/pophttp](https://github.com/brokeh/pophttp) with added support for ROS. This is to be used in conjunction to a Logi Pop smart-button, though could potentially be used by any device that communicates with a LIFX server.

This solution was motivated to get around the IFTTT time delay which prevented any soft-real-time signal to a robot. 

It may be helpful to refer to the following resources:
- [POP button FAQ](https://support.logitech.com/en_us/product/pop-smart-button/faq) when setting up the hardware or performing a factory reset.
- [POP button Getting Started](https://support.logi.com/hc/en-us/articles/360024153674--Getting-Started-POP-Home-Switch) for first time setup.

Check out a copy of the original README from the forked version [here](./FORKED_README.md). This document goes into detail regarding python setup and implementing config files. Unless you are modifying the server implementation, you should be able to leave the configuration at default.

## Steup

First start by installing the 'Logitech Pop' application on your mobile device.

Next, if this is this is a new button, then connect your mobile device to that network. Otherwise connect to the network that the button has previously been configured to. If uncertain which network or if you would like to change then check out the [FAQ](https://support.logitech.com/en_us/product/pop-smart-button/faq) to factory reset the bridge. 

Then open the application, find, and connect to the bridge. 

At this point, make sure the ROS node is running as it must present a LIFX server. Again make sure the ROS node is running on a machine connected to the same network as the button. 

Now in the application, scan for devices (specifically the LIFX server). Select this device and bind the 3-actions (single-click, long-press, and double-click) as actions to send to the server. Note: in the current implementation the values sent are ignored, however, a future version may transmit the values as a different topic.

## Run Node

To run the button node,

```
rosrun ros_pop_button pop_button_node.py
```

If button hardware is not avaliable then use the fake button node which has the same ROS topic interface but is mapped to the `Enter` button on the keyboard.

```
rosrun ros_pop_button fake_button_node.py
```
