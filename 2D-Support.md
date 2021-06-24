## Introduction

In order to accommodate 2D effects we have modified how Segment settings are used and added 2D Matrix and panel variables on the [Led Preferences](https://github.com/atuline/WLED/wiki/LED-Preferences)settings.
Note: Currently only working in dev. Segment settings currently in SEGMENT2DV2 Branch of dev. You are invited to test this and give feedback on [Beta testing discord channel](https://discord.com/channels/700041398778331156/700701772838207640)

## 2D architecture

WLED SR distinguishes between the following levels
* 2D Segment (SEGMENT2DV2 Branch)
* 2D Matrix (dev)
* 2D Panel (dev)

## 2D Segments
As WLED supports multiple segments, all effects and therefore also 2D effects are first projected on a segment. In [1D](https://github.com/Aircoookie/WLED/wiki/Segments), a segment is a zone on a LED strip and is specified by Start Led and a Stop Led.
In 2D, a segment is a rectangle on a 2D matrix and 2D effects plot on this rectangle using x,y coordinates of the SEGMENT.
In order to use the 1D segment UI to specify a segment rectangle, currently the following trick is used:

Segment top left = (start%matrixWidth, start/matrixWidth)
Segment bottom right = (stop%matrixWidth, stop/matrixWidth)

Example of 1 segment (default) covering a whole 16x16 matrix:
* start = 0, stop = 255
* top left = (0,0)
* bottom right = (15,15)
* width = height = 16

Example of a segment covering a middle part rectangle of the 16x16 matrix:
* start = 20, stop = 235
* top left = (4,1)
* bottom right = (10,14)
* width = 7
* height = 14

Example of a segment covering the left part of the 16x16 matrix:
* start = 0, stop = 241
* top left = (0,0)
* bottom right = (0,15)
* width = 1
* height = 16

Multiple segments can be specified this way