To use THS on a stem bus, you will need to begin by instantiating the following plugins, in order, at **the end** of the stem bus's insert slots:

1. YSFX
2. Blue Cat's Connector

!!! tip "Post-Fader Inserts"
    If you are using a DAW that supports post-fader inserts, I would recommend making Connector a post-fader insert on your stem buses. Doing so will allow you to use the channel fader to control the level of the stem bus and still use the channel meter when mixing.

## YSFX
First, open YSFX. By default, YSFX will look similar to the following:

![Screenshot](../img/Pasted%20image%2020260601204005.png)

To load THS, click **Load** and navigate to the folder where you saved your copy of the plugin. Select the JSFX file for THS, and then click **Open**. Once loaded, YSFX should look similar to the following:

![Screenshot](../img/Pasted%20image%2020260601204152.png)

The main parameter to pay attention to at this stage is the **Stem ID**. THS supports summing for up to 8 stem buses, and for the plugin to function correctly, each stem must be set to a unique ID. As you load THS on your stem buses, make sure to update the **Stem ID** parameter so each bus is assigned a unique value.

## Blue Cat's Connector
Next, open Blue Cat's Connector. By default, it will look like the following:

![Screenshot](../img/Pasted%20image%2020260601204539.png)

Since we are currently setting up the stem buses, you will want to enable **SEND** mode. Once enabled, Connector will look like the following:

![Screenshot](../img/Pasted%20image%2020260601204640.png)

Since we are using Connector within the same application (and not trying to send sound from one application to another), we can leave the mode set to the default of **APP**.

Connector uses an internal networking system to transmit sound between instances of the plugin. To differentiate between multiple sending instances, Connector uses the **Port** parameter. Each instance of Connector must be set to a unique **Port** value for the sender/receiver pairs to function correctly. You can also update the **Name** parameter at the bottom by double-clicking it. This serves no functional purpose but can help troubleshoot connections between sender and receiver nodes. For example, you might make the following port assignments in a project with 4 stem buses:

| Stem Bus | Port   | Name        |
| -------- | ------ | ----------- |
| 1        | `8080` | `Stem_1_TX` |
| 2        | `8081` | `Stem_2_TX` |
| 3        | `8082` | `Stem_3_TX` |
| 4        | `8083` | `Stem_4_TX` |

Repeat this process for all stem buses in your project, making sure that each instance of Connector is assigned a unique port value. Make note of the port values selected during this process as you will need them when setting up the master instance of THS. In my example, my configured Stem 1 sender appears as follows:

![Screenshot](../img/Pasted%20image%2020260601205520.png)

!!! tip "Connector Presets – Sender"
    To simplify the process of setting up THS in future projects, you can save the configurations you set for your sender instances of Connector as presets. That way, you can simply instantiate Connector on your stem buses, load each TX preset, and all your senders will be automatically configured.

## Output Routing
Unless otherwise noted in the [DAW-Specific Considerations for THS](MCM_DAW_Considerations.md), I **strongly** recommend modifying the output routing of your stem buses to prevent their sound from ending up on your master bus. How you do this will vary between DAWs. In Cubase, simply changing the output routing option to **No Bus** will do the trick:

![Screenshot](../img/Pasted%20image%2020260601210526.png)
