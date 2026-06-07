## Bitwig Studio
* **Mixed Plugin Formats:** Bitwig can simultaneously load CLAP, VST3, and VST2 plugins. Mixing different plugin formats within a single project can cause synchronization issues between the stem busses and the master bus. When setting up THS, make sure to load the VST3 version of YSFX on your stem busses and within Metaplugin on your master bus track.

??? tip "Setting Plugin Preferences in Bitwig"
    By default, Bitwig will apply its own priority scheme for the plugins displayed inside the DAW. This behavior can be modified and should be updated if you believe you have installed the CLAP and VST3 version of YSFX.

    Open Bitwig's menu, then go to **Settings**. In the menu on the left-hand side, click **Locations**. Here, Bitwig offers several options for controlling how it prioritizes plugin versions. When testing Bitwig, I selected the **All plug-ins** option to force Bitwig to display all variants of all scanned plugins:

    ![Screenshot](../img/Pasted%20image%2020260607081225.png)

## Universal Audio LUNA
* **Sleeping Tracks:** Due to the way LUNA manages its audio processing threads, any track that is not actively producing sound will likely be put to sleep. This may cause synchronization issues while using THS within LUNA.

!!! warning "Possible Synchronization Workaround for LUNA"
    Using LUNA's extension system, it may be possible to work around the sleep issue noted above. By applying the **Studer A800** tape machine to all channels with Noise **enabled**, and applying the **ATR-102** tape machine to all busses (including the main output) with Noise **enabled**, all tracks within the project will remain "silently" activated. Further testing is required.