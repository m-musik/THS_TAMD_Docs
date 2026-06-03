Both THS and TAM/TAMD leverage the principle of channels being fed into stem buses that ultimately feed into a master bus. To get the most out of these plugins, you will need to organize your project in a similar manner.

In the example shown below, I have created four stem groups in Cubase 15, each of which contains 3 tracks (channels) that are routed to their corresponding stem (bus):

![Screenshot](../img/Pasted%20image%2020260601202319.png)

In Cubase 15, you can create folders that are also group tracks that can have the output of other tracks routed to them. If you are using an older version of Cubase or a different DAW, you will need to follow an appropriate procedure for creating a bus and manually route the appropriate tracks to your buses. Essentially, all individual tracks should reach the master bus in the following way:

$$
\text{Track} \rightarrow \text{Stem Bus} \rightarrow \text{Master Bus}
$$

Note that the Master Bus can be either your DAW's Stereo Output track, or a separate bus that all Stem Buses are routed to. Either configuration will work.