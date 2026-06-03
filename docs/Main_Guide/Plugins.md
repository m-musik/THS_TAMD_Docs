To use THS and TAM/TAMD as described in this guide, the following tools are needed:

## First-Party Plugins
THS and TAM/TAMD are saved as JSFX source code files. These can be stored and loaded from any location, but should ideally be kept in a folder that will ensure the plugin files will not be inadvertently modified or moved in the future.

### Free Plugins
THS and TAM can be obtained from [DocShadrach's Github repository](https://github.com/DocShadrach/MyReaperFXs) at the following links:

* **[The Hot Summer on Github](https://github.com/DocShadrach/MyReaperFXs/blob/main/The_Hot_Summer.jsfx)**
* **[The Analog Molecule on Github](https://github.com/DocShadrach/MyReaperFXs/blob/main/The_Analog_Molecule.jsfx)**

### Paid Plugins
TAMD, the deluxe version of TAM, can be purchased from [DocShadrach's Ko-Fi shop](https://ko-fi.com/docshadrach/shop) at the following link:

* **[The Analog Molecule Deluxe on Ko-Fi](https://ko-fi.com/s/e46fdb9a07)**

## Third-Party Plugins

### For All Methods
* **[YSFX](https://github.com/JoepVanlier/ysfx)[^1]:** This plugin allows you to use JSFX plugins in any DAW, not just Reaper. You can either download prebuilt versions of the plugin from the Github repository's [Releases page](https://github.com/JoepVanlier/ysfx/releases), or clone and build the plugin from source.

### Metaplugin and Connector Method
* **[DDMF Metaplugin](https://ddmf.eu/metaplugin-chainer-vst-au-rtas-aax-wrapper/):** This plugin is a plugin wrapper that can instantiate other plugins inside of itself. Metaplugin is used to host the instance of YSFX that operates THS in Master mode.
* **[Blue Cat's Connector](https://www.bluecataudio.com/Products/Product_Connector/)[^2]:** This plugin is used to send the stem bus outputs to Metaplugin using a sender and receiver structure.

!!! info "Plugin Demos"
    Demos are available for Metaplugin and Connector. These can be used to test the Metaplugin and Connector method without needing to purchase the plugins first. Metaplugin's demo is fully functional but its state cannot be saved. Connector's demo limits you to 5 total instances of the plugin at any given time. Combined, this will allow you to route two stem buses to a master instance of THS.

[^1]: Based on community testing and feedback, it appears that the latest version of YSFX requires a fairly modern version of macOS. Users seem to have the most success on macOS 26 (Tahoe), but other recent versions of macOS may also work.
[^2]: While Metaplugin can technically send and receive audio in a similar manner as Connector, as of the time this guide was drafted, the SendIt node in Metaplugin produces crackling audio. Connector is recommended as a more reliable alternative at this time.