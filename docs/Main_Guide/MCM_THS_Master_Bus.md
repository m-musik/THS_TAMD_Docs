## General Setup
To use THS on the master bus, you will need to begin by instantiating Metaplugin as the **first** insert on your master bus. When you first open Metaplugin, it will resemble the following:

![Screenshot](../img/Pasted%20image%2020260601210955.png)

Begin by loading YSFX. You can do this manually by right-clicking anywhere in the grey area of Metaplugin, then clicking **Load plugin from file...**, or by clicking **Options...** in the bottom-left corner of the plugin and selecting any of the available scan options to populate the **Plugin library**. Then search for YSFX in the plugin list and drag-and-drop it onto the canvas. Once loaded, YSFX will appear as follows:

![Screenshot](../img/Pasted%20image%2020260601211400.png)

In Metaplugin, the pins on the top of all plugin nodes are considered to be the inputs, and the pins on the bottom are the outputs. The channel numbers increase from left to right, so the first two pins on the top and bottom are your "normal" stereo input and output pins. We can begin by connecting the first two pins on the bottom of YSFX to the two pins of the Audio Output node to connect what will eventually be the output of THS to the output of Metaplugin:

![Screenshot](../img/Pasted%20image%2020260601211615.png)

## Blue Cat's Connector
Next, load enough instances of Blue Cat's Connector to receive sound from all the stem busses in your project. In my example, I have four stem busses, so I will load 4 instances of Connector:

![Screenshot](../img/Pasted%20image%2020260601211805.png)

Next, we will connect the outputs of the Connector instances to the appropriate inputs of YSFX. This is the step that enables use of THS outside of Reaper as most DAWs do not allow for arbitrary routing of many channels the way we can in Metaplugin. It's also important to note that THS expects the stem bus inputs to begin on Channels 3-4, ***not*** Channels 1-2. This means that when we connect the Connector instances to YSFX, we will skip the first two input pins and begin our connections with the second set of pins:

![Screenshot](../img/Pasted%20image%2020260601212243.png)

!!! tip "Moving Nodes in Metaplugin"
    Nodes can be rearranged and moved within Metaplugin at any time. Feel free to rearrange and move them as desired to improve the legibility of the connectivity graph.

We can now begin to configure the Connector instances to receive sound from the senders we previously instantiated on the stem busses. Before proceeding, it's critical to understand the channel assignments THS expects the stem busses to follow:

| **Stem** | **Channel Assignment** |
| -------- | ---------------------- |
| 1        | 3-4                    |
| 2        | 5-6                    |
| 3        | 7-8                    |
| 4        | 9-10                   |
| 5        | 11-12                  |
| 6        | 13-14                  |
| 7        | 15-16                  |
| 8        | 17-18                  |

Based on the connection diagram we've created, this means that, from left to right, our Connector instances will be used for stems 1, 2, 3, and 4.

Begin by opening the Connector instance connected to input pins 3-4 of YSFX. This will be the Stem 1 receiver. By default, Connector will appear as follows:

![Screenshot](../img/Pasted%20image%2020260601213229.png)

Begin by enabling **RCV** mode. Connector will then appear as follows:

![Screenshot](../img/Pasted%20image%2020260601213327.png)

Since we previously setup all our sender nodes and started with the default port assignment of `8080`, this instance of Connector will immediately establish a connection with our Stem 1 sender. Since we named that instance `Stem_1_TX`, we get a visual indicator of the sending instance's name just below **RECEIVE FROM**. This can be a very handy tool for troubleshooting connections if you run into problems. Optionally, we can update the **Name** parameter of our new receiver node. This will make it so the sender node shows something other than `Anonymous` below its analogous **SEND TO** indicator. Here, we will name the Connector instance `Stem_1_RX` (receive):

![Screenshot](../img/Pasted%20image%2020260601213707.png)

Next, open the Connector instance connected to input pins 5-6 of YSFX. This will be the Stem 2 receiver. Then, enable **RCV** mode. Connector will now look like the following:

![Screenshot](../img/Pasted%20image%2020260601213917.png)

Unlike the first Connector receiver, this instance will not automatically connect to the next stem. To make the connection, we need to set the **Port** parameter to match the value assigned to the Stem 2 sender. If you followed the example from above, the correct port will be `8081`. Once we set **Port** to `8081` and press Enter, Connector will immediately establish a connection to the Stem 2 sender that we named `Stem_2_TX`:

![Screenshot](../img/Pasted%20image%2020260601214119.png)

Repeat this process for as many stems as you would like to route into THS, up to the maximum of 8 stems.

!!! tip Connector Presets – Receiver
    To simplify the process of setting up THS in future projects, you can save the configurations you set for your receiver instances of Connector as presets. That way, you can simply recall the presets to configure your receiver instances of Connector.

## YSFX
Now that we have connected and configured all the receiver instances of Connector, we can configure the master instance of THS. Double-click the YSFX node in Metaplugin. By default, it will look like the following:

![Screenshot](../img/Pasted%20image%2020260601214615.png)

Begin by loading THS, which will initially look like the following:

![Screenshot](../img/Pasted%20image%2020260601214656.png)

Since this is our master instance of THS, we can now change the **Topology** parameter from _Stem Sender (Bus)_ to **_Master Summer (Main)_**. Once this parameter has changed, THS should now appear as follows:

![Screenshot](../img/Pasted%20image%2020260601214818.png)

Assuming all stem bus instances of THS have been configured correctly, you should see a dim green indicator next to each configured stem. If you believe you should have more green indicators than what you currently see, revisit the **Stem ID** assignment of your stem bus instances of THS to verify that each stem is assigned a unique ID.

To verify that THS is fully configured and ready for use, play some sound through your project's stem busses. In Cubase, I can do this by instantiating the TestGenerator plugin to play test tones. If everything is working correctly, the green indicators in the master bus instance of THS should begin to flash bright green. This means that THS is detecting signal input from each bus. If everything was configured correctly, the indicator for all configured and connected channels should periodically flash while playing sound.

If any of the channel indicators are not blinking, go back and verify the configuration for your sender and receiver nodes of Connector. If the sender/receiver pairs are configured correctly, the level meter on the right-hand side of your Connector receivers will show signal:

![Screenshot](../img/Pasted%20image%2020260601215608.png)

!!! tip "Metaplugin Presets"
    To simplify the process of setting up THS in future projects, you can save your Metaplugin setup by clicking the **User presets** tab, then click **Save new preset**. This will save all the parameters and connections for the plugins in your diagram and can significantly reduce the time needed to setup the master instance of THS.

## Next Steps
After completing the procedure documented on this page, THS should be fully configured for operation in your DAW using the Metaplugin and Connector Method!

If you wish to add TAM(D) to your project, you can proceed to the [Channels](TAMD_Channels.md) setup page. I would also strongly encourage you to review the TAM(D) [DAW-Specific Considerations](TAMD_DAW_Considerations.md) page so you are aware of any DAW-specific constraints that may affect your use of TAM(D).