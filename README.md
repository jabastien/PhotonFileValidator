# Photon File Viewer
A file viewer application for AnyCubic Photon sliced files (*.photon and *.cbddlp). The viewer can show you preview images, print information and all layers with information on overhang and islands issues.

![Main screen](https://github.com/Photonsters/PhotonFileViewer/raw/master/doc/screen1.png)

## Photon files

### TL;DR
Basic information, with this application you can:
- View all layers of a sliced (AnyCubic Photon Slicer or ChiTu DLP Slicer) file for the Photon 3D printer.
- Easy see overhangs and unsupported areas (color coded in yellow and red)
- Change exposure, off time and buttom layer settings on already sliced files.
- Easy check if any part of a model is to close to the border
- Quickly jump to problem layers and watch if it will break your prints.

### What is a Photon file
A Photon file is generated by the AnyCubic Photon Slicer (rebrand of ChiTu DLP Slicer). The slicer takes a 3D object and turn it into a list of images, each representing
one printable layer. The 3D printer then prints each layer by exposing liquid resin with UV light, and lifting the build plate to peel off the model from the bottom plastic (FEP).

The Photon file also contains information about the height of each layer, for how long each layer is exposed to UV light, and some settings for overexposing the first layers to make the print stick to the build plate.

### Why do I want to view a photon file
In the ideal world, - you don't. The slicer makes the file, and the printer use the file to print your object.

But, sometimes prints fail.

There are a lot of reasons why prints are failing.

- Missing or weak support. When the printer is done printing one layer, the layer is lifted off the botom plastic film (FEP). The support must be strong enough to support the lift (pull).
- Wrong exposure or off time settings. Each Resin is different in the chemical content, so each resin have a limited time range where it cures each layer.
- Separated Resin. Most resin needs to be shaken or stirred befor use, which ensures that the resin compunds are mixed in the correct manor.
- File, model or slicing errors. Applications have bugs, so errors could be intruduced in the process.
- Printer errors. When buying a budget printer, some will only pass the quality control on a good day. Some components might be designed with no fault margin, introducing periodic errors (like the power supply and the LCD).
- Temperature, if the resin is to cold it will not flow under the model between the layers, if to hot it will have issues with overcuring.

The Photon File Viewer can help you by showing all the layers in full resolution and all settings stored in the file.

The Viewer can also analyze the file for layers that contains areas that is not supported (printed in mid-air, called islands). Islands are a problem, because the model will not be printed as designed.
In the best scenario the island will stick to the plastic bottom of the printer or attach itself to the printed model, but if you are unlucky - it could be trapped between the printer and the model, breaking the FEP or the LCD screen.


## Installation
If you already have Java installed, you can simply download the jar file and execute it (dobbeltclick or from command line: java -jar PhotonFileCheck.jar

[Download Jar version](https://github.com/Photonsters/PhotonFileViewer/raw/master/release/photonfileviewer-1.0.zip)


### Install on Windows
![Windows Main screen](https://github.com/Photonsters/PhotonFileViewer/raw/master/doc/windows.png)

The windows installer is not signed, so you have to go through some warning pages before you are allowed to install it.

[Download Windows version](https://github.com/Photonsters/PhotonFileViewer/raw/master/release/photonfileviewer-1.0-windows-installer.exe)


### Install on macOS
Download the zip and unpack it, then run the installer. The installer is not signed, so you may have to locate the installer in finder and right click on it and select open.

[Download Mac version](https://github.com/Photonsters/PhotonFileViewer/raw/master/release/photonfileviewer-1.0-osx-installer.zip)

### Install on Linux
The linux installer is build from the same source, but not tested. Feel free to test and provide feedback.

[Download Linux version](https://github.com/Photonsters/PhotonFileViewer/raw/master/release/release/photonfileviewer-1.0-linux-installer.run)

## Usage

### Open a slice file
With the open button you can browse your local file system for files with the .photon file extension. When a file has been selected, it will load the file.

During load, it will translate each layer to an image and check you file for overhangs and unsupported areas. The application will update status information so you can follow the process.

When the load is done, it will show layer 0, which is the first layer the printer will print. If will also show if the model extends beyond the border or have islands.

## Save the file
If you want to try printing the file with other settings, select the save button. In the save dialog you will be able to change the file name, the normal exposure time, the off time, the bottom layers count and the bottom layer exposure time.

## Show Information
With the show information button you can see the following information:

- Build area set in the file, should be 68.4 * 120.96 mm for the Photon printer.
- Resolution of the printer, should be 1440 * 2560 pixels for the Photon printer.
- Print information

The Print information contains the layer height, the total number of pixels on all layers, the *extimated volume of resin* to be used and the *time* it will take to print it.

## Jump to layers with to large model areas.
If you set a safty border margin, each layer is check for areas that expand outside the margin. The application will show a list of the first layers. Use the >> button to jump to the next layer. If there are no more layers, it will go back to the first again.

## Jump to layers with islands
If you model contains islands, if will show a list with the first layer numbers. With the >> button you can quickly jump to the next layer that contains islands.

As small islands can be hard to find, the application will draw horizontal and vertical cross lines to help you locate the islands. If the island area are very big, no cross lines will be drawn.

## Show previews
The slicer produces preview images that is used by the printer to help you select the correct model to print. You can also see the preview images in the file viewer application.

## Print Margin
You can optional set a safety margin. When a safty margin is set, the application will check that all model layers is not printed outside the margin.

The margin is set in pixels (0.04725mm) and you find the settings in the file photon.properties in the folder where the jar file is installed. You can edit the file with a text editor.

The default is: margin=0

## Time calculations
In the information dialog you can see the estimated time for the print. The Photon slicer is known (versions 1.3.6 and before) for showing false print times. The reason is that the application is not including the peel time (the time is takes to remove the model from the FEB). On a standard Photon printer the peel time is 5.5 seconds.

If you modify the Photon printer to have faster or slower peel time, so to handle this you can change the settings used to calculate the time. You find the settings in photon.properties file where the jar is installed.

The default is: peel=5.5


### Command line usage
You can use the application from the command line: java -jar PhotonFileCheck.jar

You can add a Photon slice file name as argument, and the file will be loaded when the application starts.

## Developer Information

### Source code layout

### Code Implementation

