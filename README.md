# Godot OpenVR GDNative module
This module is provided as is, all files are contained within the addons/godot-openvr-asset folder

The scenes subfolder contains a number of godot scenes that help you set up your project. 
For basic functionality start with adding ovr_first_person.tcn to your project.
Also make sure that vsync is turned off in your project settings.

Using the main viewport
-----------------------
The ARVR server module requires a viewport to be configured as the ARVR viewport. If you chose to use the main viewport an aspect ratio corrected copy of the left eye will be rendered to the viewport automatically.

You will need to add the following code to a script on your root node:

```
var interface = find_interface("OpenVR")
if interface and interface.initialize():
	get_viewport().arvr = true
	get_viewport().hdr = false
```

Using a separate viewport
-------------------------
If you want control over the output on screen so you can show something independent on the desktop you can add a viewport to your scene and set the arvr property to true and hdr property to false. It is important that the ARVR nodes are child nodes within this viewport. You can add a normal camera to your scene to render a spectator view or turn the main viewport into a 2D viewport and save some rendering overhead.

You can now simplify you initialisation code on your root node to:

```
var interface = find_interface("OpenVR")
if interface:
	interface.initialize()
```

(note that this is still experimental)

HDR support
-----------
HDR support for the headset is currently not available. OpenVR does not accept Godots HDR color buffer for rendering. We're still investigating this.

Licensing
---------
The Godot OpenVR module and the godot scenes in this add on are all supplied under an "unlicense".

The dynamic libraries supplier by Valve fall under Valve's own license. For more information about this license please visit https://github.com/ValveSoftware/openvr
