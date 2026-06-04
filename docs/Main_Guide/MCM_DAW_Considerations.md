## Logic Pro
* Due to the way Logic Pro sandboxes plugins, you will need to set your Connector instances to **LOCAL HOST** mode instead of **APP** for sound to be transmitted between sender and receiver nodes.[^1]
* Due to the way Logic Pro manages its audio processing threads, any track that is not actively producing sound will likely be put to sleep. This may cause synchronization issues while using THS within Logic.
* When setting up your stem buses in Logic, you should **NOT** remove the output assignment for your stem buses. Doing so may interfere with Connector's ability to transmit sound to the receiver instances inside Metaplugin.

[^1]: Discovered by apan of Gearspace.