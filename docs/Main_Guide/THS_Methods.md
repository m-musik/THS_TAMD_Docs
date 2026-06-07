## Universal Methods
As of the time the current version of this guide was published, the following connectivity methods have been discovered for operating THS outside of Reaper:

* **Metaplugin and Connector Method:** Utilizes DDMF's Metaplugin and Blue Cat's Connector plugin to route the output of a project's stem busses to the appropriate inputs of the YSFX plugin running THS in master mode.
* **Sidechain Method[^1]:** Utilizes the DAW's native multi-sidechain input feature to route the output of a project's stem busses directly to the sidechain inputs of the YSFX plugin running THS in master mode.

You are free to use whichever connection method you would like for THS. Note that not all DAWs support the Sidechain Method, so you may find that you need to use the Metaplugin and Connector Method instead.

Regardless of the connectivity method chosen, I **strongly** encourage you to review the DAW-Specific Considerations page for your selected method before following the guide. It may contain special notes or workarounds for your DAW that are needed for the method to function correctly.

## DAW-Specific Methods
In addition to the base methods, some DAWs may require special procedures that are unique to each DAW. Currently, the following DAWs have dedicated procedures that must be followed instead of the base methods:

* **Logic Pro (10.7.9 or newer):** Starting around Logic Pro 10.7.9, Apple introduced a new scheduling algorithm that aggressively halts processing on any track that Logic believes will not contribute to the output of the project. This primarily affects self-generating plugins that can produce sound without an audio or MIDI event on the track. It also affects THS as it depends upon a continuous stream of audio blocks to operate correctly.

[^1]: Discovered and shared by Charlie_N and Justus1234 of Gearspace.