### User Interface
* Info Page: status info for soundreactive (similar to upstream 0.14.0)
* Info Page: basic hardware info added (similar to MoonModules 0.14.0)

### Audio Processing
(tbw softhack007)

### UDP sound sync
* Support for receiving "V2" format, which is sent by upstream 0.14.0 

### Effects
* Minor bugfixes, like missed pixels in "Stream" effects
* Sanity check added in setPixelColor(), to avoid memory errors due to negative pixel index
* * NB: this change also affects realtime modes (DDP, DMX, E13.1, LedFx, ...)


### Custom Effects, 2D/3D, live preview
(tbw ewowi)


## various bugfixes from upstream 0.14.0
* auto-reboot after cfg.json restore (to avoid that WLED directly overwrites them after upload)
(tbw softhack007)

## Changes from upstream v0.13.3
* Fixed flickering
* Fixed boot issues on new installs
* Added support for LPD6803
