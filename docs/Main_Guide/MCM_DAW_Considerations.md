## Universal Audio LUNA
* Due to the way LUNA manages its audio processing threads, any track that is not actively producing sound will likely be put to sleep. This may cause synchronization issues while using THS within LUNA.

!!! warning "Possible Synchronization Workaround for LUNA"
    Using LUNA's extension system, it may be possible to work around the sleep issue noted above. By applying the **Studer A800** tape machine to all channels with Noise **enabled**, and applying the **ATR-102** tape machine to all busses (including the main output) with Noise **enabled**, all tracks within the project will remain "silently" activated. Further testing is required.