## All DAWs
### Link Loss
You may experience issues with TAM(D) forgetting your last selected Link setting for the channels, busses, and master bus upon opening your project. You can open any instance of TAM(D) and reengage the link function as desired.

## Logic Pro (10.7.9 or newer)
### Project Setup
**Before setting up TAM(D), users of Logic Pro 10.7.9 or newer must follow the [Project Setup](LP_Setup.md) and [Track](LP_Tracks.md) setup pages from the Logic Pro-specific THS guide.** If you are working in Logic Pro and have already setup THS, you do not need to repeat those steps.

Starting around Logic Pro 10.7.9, Apple introduced a new scheduling algorithm that aggressively halts processing on any track that Logic believes will not contribute to the output of the project. This primarily affects self-generating plugins that can produce sound without an audio or MIDI event on the track. It also affects TAM(D) as it depends upon a continuous stream of audio blocks to operate correctly.

### Placement of TAM(D) Channels
Since Logic requires an instance of your selected plugin wrapper as the **first** Audio FX on all base tracks to keep them awake for processing, TAM(D) should be placed as the **second** effect on all tracks instead of the first, immediately following your plugin wrapper.

### Synchronization
You may experience synchronization issues upon opening a Logic project containing TAM(D), even after following the current best procedure. To work around this, start and stop playback of your project once after opening the project. All instances of TAM(D) should remain synchronized for the rest of the time you have the project open.

## Universal Audio LUNA
* Due to the way LUNA manages its audio processing threads, any track that is not actively producing sound will likely be put to sleep. This may cause synchronization issues while using TAM(D) within LUNA.

!!! warning "Possible Synchronization Workaround for LUNA"
    Using LUNA's extension system, it may be possible to work around the sleep issue noted above. By applying the **Studer A800** tape machine to all channels with Noise **enabled**, and applying the **ATR-102** tape machine to all busses (including the main output) with Noise **enabled**, all tracks within the project will remain "silently" activated. Further testing is required.