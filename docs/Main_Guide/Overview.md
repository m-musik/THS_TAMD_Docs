The purpose of this guide is to explain how to use DocShadrach's The Hot Summer (THS) and The Analog Molecule (TAM) / The Analog Molecule Deluxe (TAMD) JSFX plugins outside of Reaper. This guide was originally written from the perspective of a Cubase Pro 15 user, but has been expanded to cover other DAWs as well.

The procedures documented here are current as of the time the guide was published and are not a comprehensive reference for all possible ways of operating these plugins. Feel free to use and adapt this guide to best suit your needs!

## Tested DAWs
The procedures documented in this guide have been tested in the following DAWs:

| DAW           | TAM(D) | THS: Metaplugin and Connector Method | THS: Sidechain Method | THS: DAW-Specific Method | Versions Tested |
| ------------- | :----: | :----------------------------------: | :-------------------: | :----------------------: | --------------- |
| Cubase        | ✅ | ✅ | ✅ | N/A | <ul><li>Pro 15</li></ul> |
| Logic Pro     | ⚠️ | ⚠️ | ❌ | Yes | <ul><li>12.2</li></ul> |
| Ableton       | ✅ | ✅ | ✅ | N/A | **TBD** |
| Fender Studio | ✅ | ✅ | ✅ | N/A | **TBD** |
| UAD LUNA      | ⚠️ | ⚠️ | ❌ | ❓ | <ul><li>2.0.3</li></ul> |
| Bitwig Studio | ❓ | ❓ | ❓ | ❓ | **TBD** |

??? note "Table Key"
    ✅ = Tested as working<br>
    ⚠️ = Works with caveats (for example, a DAW-specific procedure)<br>
    ❌ = Not supported<br>
    ❓ = Under investigation

Just because your DAW is not listed above does not mean it is unsupported! By adapting the procedures documented in this guide, you may be able to find a way to make THS and TAM(D) run in your DAW, too. It may also be possible to find workarounds for DAWs that currently face issues when using these plugins.

## Navigating the Guide
This guide has been written using MkDocs and the Material for MkDocs theme. This provides handy navigation features, including next and previous links at the bottom of each page. You can use these links to navigate through the guide without needing to manually interact with the navigation menu. If you should want to visit a specific section, you can navigate to it directly via the menu.

Additionally, each page features a table of contents that can be used to jump between major sections of each page. Each page of this guide, and each major section of each page, can be linked to directly for quick recall or sharing.