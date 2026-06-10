## General Setup
To use THS on the master bus, you will need to begin by instantiating your plugin wrapper as the **first** insert on your master bus.

=== "Metaplugin"
    When you first open Metaplugin, it will resemble the following:
    
    ![Screenshot](../img/Pasted%20image%2020260606204958.png)
    
    Begin by loading YSFX. You can do this manually by right-clicking anywhere in the grey area of Metaplugin, then clicking **Load plugin from file...**, or by clicking **Options...** in the bottom-left corner of the plugin and selecting any of the available scan options to populate the **Plugin library**. Then search for YSFX in the plugin list and drag-and-drop it onto the canvas. Once loaded, YSFX will appear as follows:
    
    ![Screenshot](../img/Pasted%20image%2020260606205112.png)
    
    Next, right-click anywhere in the grey area of Metaplugin and click the **FourChanMixer** option. This will add a four-channel mixer node to the graph:
    
    ![Screenshot](../img/Pasted%20image%2020260606205123.png)
    
    In Metaplugin, the pins on the top of all plugin nodes are considered to be the inputs, and the pins on the bottom are the outputs. The channel numbers increase from left to right, so the first two pins on the top and bottom are your "normal" stereo input and output pins. We can begin by connecting the first two pins on the bottom of YSFX to the pins 3-4 of the FourChanMixer node. To make use of the same sidechain synchronization tone used on the individual tracks of the project, we will also connect pins 3-4 of the Audio Input node to pins 1-2 of the FourChanMixer node:
    
    ![Screenshot](../img/Pasted%20image%2020260606205159.png)
    
    Double-click the FourChanMixer node to open the mixer controls. Since we are only using the first two channels, we can mute the third and fourth channels. Additionally, we can leverage the mixer's level control to attenuate channel 1 by -80 dB:
    
    ![Screenshot](../img/Pasted%20image%2020260606205209.png)
    
    This will reduce the level of the sidechain input by an additional 80 dB for a cumulative attenuation of -272 dB.
    
    !!! tip "Moving Nodes in Metaplugin"
        Nodes can be rearranged and moved within Metaplugin at any time. Feel free to rearrange and move them as desired to improve the legibility of the connectivity graph.

=== "Element"
    When you first open Element, it will resemble the following:
    
    ![Screenshot](../img/Pasted%20image%2020260609220533.png)
    
    Begin by loading YSFX. If this is your first time using Element, you can load YSFX by right-clicking anywhere in the grey area of Element, then hover over **Unverified**. Then hover over the plugin format that matches your host DAW's preferred format. Scroll through the list and search for the `ysfx-s FX` plugin, then click it. Otherwise, hover over **Jean Pierre Cimilando / Joep Vanlier** and click the variant of YSFX that matches your host DAW's preferred format. Once loaded, YSFX will appear as follows:
    
    ![Screenshot](../img/Pasted%20image%2020260609220554.png)
    
    !!! warning "Mixing Plugin Formats"
        When adding your wrapper and router plugins to Element, make sure to select the same format as the plugins used by your host DAW. For example, if you are using Cubase, make sure you select VST3 plugins. If you are using Logic, select AU plugins instead. Mixing plugin formats can cause synchronization issues.
    
    Next, right-click in the grey area of the plugin, hover over **Element**, and click the **Audio Mixer** option. This will add a four-channel mixer to the node graph:
    
    ![Screenshot](../img/Pasted%20image%2020260609220631.png)
    
    !!! tip "Moving Nodes in Element"
        Nodes can be rearranged and moved within Element at any time. Feel free to rearrange and move them as desired to improve the legibility of the connectivity graph.
    
    To make use of the synchronization tone, we are going to route the plugin's sidechain input into the four-channel mixer, along with the main stereo output of YSFX. By default, Element only has two input pins, so we must add two more pins to accept a sidechain input. To do this, double-click the **GRAPH** tab on the left side of the plugin. Then, click the **plus button (+)** next to Audio Ins until it shows a value of 4. The Audio In node will update and should now have 4 pins:
    
    ![Screenshot](../img/Pasted%20image%2020260609220659.png)
    
    In Element, the pins on the top of all plugin nodes are considered to be the inputs, and the pins on the bottom are the outputs. The channel numbers increase from left to right, so the first two pins on the top and bottom are your "normal" stereo input and output pins. We can now make the following connections in our graph: 
    
    * Connect pins 3-4 of the Audio In node to input pins 1-2 of the Audio Mixer
    * Connect output pins 1-2 of YSFX to input pins 3-4 of the Audio Mixer
    * Connect output pins 1-2 of the Audio Mixer to pins 1-2 of the Audio Out node
    
    When connected, your node graph should resemble the following:
    
    ![Screenshot](../img/Pasted%20image%2020260609221056.png)
    
    Before we can adjust the mixer, we need to connect the synchronization tone to Element as its sidechain input:
    
    ![Screenshot](../img/Pasted%20image%2020260609221300.png)
    
    Once `SYNC_TONE` is connected as the sidechain input, start and stop playback in the DAW one time to wake the track. Note that Element has its own set of transport controls inside the plugin and these are not connected to Logic. You will need to be sure to click out of or close Element before starting and stopping playback.
    
    Next, double-click the Audio Mixer node to open the mixer controls. Since we are only using the first two channels, we can mute the third and fourth channels. Additionally, we can leverage the mixer's level control to attenuate channel 1 by -90 dB:
    
    ![Screenshot](../img/Pasted%20image%2020260609221818.png)
    
    This will reduce the level of the sidechain input by an additional 90 dB for a cumulative attenuation of -282 dB.
    
## Router Plugin
=== "Blue Cat's Connector"    
    Next, load enough instances of Blue Cat's Connector to receive sound from all the stem busses in your project. I have four stem busses in my example, so I will load 4 instances of Connector:
    
    === "Metaplugin"
        ![Screenshot](../img/Pasted%20image%2020260606205248.png)
    
    === "Element"
        ![Screenshot](../img/Pasted%20image%2020260609221338.png)
    
    Next, we will connect the outputs of the Connector instances to the appropriate inputs of YSFX. This is the step that enables use of THS outside of Reaper as most DAWs do not allow for arbitrary routing of many channels the way we can in wrappers like Metaplugin and Element. It's also important to note that THS expects the stem bus inputs to begin on Channels 3-4, ***not*** Channels 1-2. This means that when we connect the Connector instances to YSFX, we will skip the first two input pins and begin our connections with the second set of pins:
    
    === "Metaplugin"
        ![Screenshot](../img/Pasted%20image%2020260606205438.png)
    
    === "Element"
        ![Screenshot](../img/Pasted%20image%2020260609221448.png)
    
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
    
    !!! tip "Connector Presets – Receiver"
        To simplify the process of setting up THS in future projects, you can save the configurations you set for your receiver instances of Connector as presets. That way, you can simply recall the presets to configure your receiver instances of Connector.

=== "Other Router"
    When a new router plugin is identified, it will be documented here!

## Connect Sidechain
=== "Metaplugin"
    Now that the receiver instances of Connector have been configured, we can set the `SYNC_TONE` track as the sidechain input for the plugin wrapper:
    
    ![Screenshot](../img/Pasted%20image%2020260606210248.png)

    Once set, start and stop playback in Logic one time to ensure all tracks are alive and synchronized.

=== "Element"
    The sidechain was already connected when setting up the node graph, so you can skip this step!

## YSFX
Now that all tracks are alive, we can configure the master instance of THS. Double-click the YSFX node in your plugin wrapper. By default, it will look like the following:

![Screenshot](../img/Pasted%20image%2020260601214615.png)

Begin by loading THS, which will initially look like the following:

![Screenshot](../img/Pasted%20image%2020260601214656.png)

Since this is our master instance of THS, we can now change the **Topology** parameter from _Stem Sender (Bus)_ to **_Master Summer (Main)_**. Once this parameter has changed, THS should now appear as follows:

![Screenshot](../img/Pasted%20image%2020260601214818.png)

Assuming all stem bus instances of THS have been configured correctly, you should see a dim green indicator next to each configured stem. If you believe you should have more green indicators than what you currently see, revisit the **Stem ID** assignment of your stem bus instances of THS to verify that each stem is assigned a unique ID.

To verify that THS is fully configured and ready for use, play some sound through your project's stem busses. In Logic, you can do this by instantiating the Test Oscillator plugin to play test tones. If everything is working correctly, the green indicators in the master bus instance of THS should begin to flash bright green. This means that THS is detecting signal input from each bus. If everything was configured correctly, the indicator for all configured and connected channels should periodically flash while playing sound.

If any of the channel indicators are not blinking, go back and verify the configuration for your router plugin.

=== "Blue Cat's Connector"
    If the sender/receiver pairs of Connector are configured correctly, the level meter on the right-hand side of your Connector receivers will show signal:
    
    ![Screenshot](../img/Pasted%20image%2020260601215608.png)

=== "Other Router"
    When a new router plugin is identified, it will be documented here!

Once verified as functional, consider saving the state of your plugin wrapper as a preset.

=== "Metaplugin"
    !!! tip "Metaplugin Presets"
        To simplify the process of setting up THS in future projects, you can save your Metaplugin setup by clicking the **User presets** tab, then click **Save new preset**. This will save all the parameters and connections for the plugins in your diagram and can significantly reduce the time needed to setup the master instance of THS.

=== "Element"
    !!! tip "Element Sessions"
        To simplify the process of setting up THS in future projects, you can save your Element setup by clicking the hamburger menu icon in the top right corner of the plugin, then click **Save Session As...**. This will save all the parameters and connections for the plugins in your diagram and can significantly reduce the time needed to setup the master instance of THS.

## Next Steps
After completing the procedure documented on this page, THS should be fully configured for operation in Logic Pro!

If you wish to add TAM(D) to your project, you can proceed to the [Channels](TAMD_Channels.md) setup page. I would also strongly encourage you to review the TAM(D) [DAW-Specific Considerations](TAMD_DAW_Considerations.md) page so you are aware of any DAW-specific constraints that may affect your use of TAM(D).