# OpenTimelineIO Import/Export Plugin for Hiero and Nuke Studio
![Supported Versions](https://img.shields.io/badge/OpenTimelineIO-0.13+-green.svg)

Import and export `.otio` files directly from Hiero or Nuke Studio


## Features

* Multiple tracks
* Tags
* Markers
* Simple re-time (reverese, constant slowdown, constant speedup)
* Fade in/out and cross dissolves
* Nested sequences are created separately and replaced with gaps in the main sequence.
* Linked audio/video when clip shares same media source
   

## Requirements

Make sure you have OpenTimelineIO (OTIO) installed on your computer before you
install the plugin. The easiest way to install OTIO is through pip.
``` bash
pip install opentimelineio
```

You may also install OpenTimelineIO by using the python version which ships
with Hiero|NukeStudio. Replace the python version in the example below with the
one you find in the applications root folder.

```bash
# Example using python 3 shipped with Nuke13+
python3 -m pip install opentimelineio
```

If you installed OTIO in another way, please make sure you have OTIO's 
python package available in the `PYTHONPATH` environment variable.


## Plugin Installation

The easiest way to install the plugin is to unpack the contents to the `.nuke` 
folder in your "HOME" directory.<br>
For Hiero/Nuke Studio version < 12 extract to the `.hiero` folder.

```bash
~/.nuke/Python/Startup/otioexporter
~/.nuke/Python/StartupUI/otioimporter
```

If you choose to install the plugin to another location, make sure to append 
the full path of the folder containing the `Python` folder to the 
`HIERO_PLUGIN_PATH` environment variable.

```bash
export HIERO_PLUGIN_PATH=/my/shared/plugin/folder
```
 

## Usage OTIO Import

Right click in a project bin and select `"Import->Import OTIO"`

![Import Bin](_static/import_bin.png "Import OTIO from project bin view")

Or you can add tracks to an existing sequence

![Import Sequence](_static/import_sequence.png "Import OTIO from a sequence")


## Usage OTIOExportTask

In Hiero's export dialog choose `"Process as Sequence"` and create a new preset 
called `"OTIO Export"`.<br>
Add a new **PATH** and choose `"OTIO Exporter"` from the list of available 
exporters in the **CONTENT** column.<br> 
Make sure to either use the `{ext}` token or end your filename with an 
`.otio` extension.<br>
The `"include tags"` checkbox toggles inclusion of tags assigned to clips in 
the OTIO metadata.<br>

![Export Sequence](_static/export_settings.png "Export OTIO file")

You may either export entire sequences or selected items in a sequence.


## Known Limitations

* Tags/markers are applied to both clips and track items on import if no 
  metadata indicates source type. 
