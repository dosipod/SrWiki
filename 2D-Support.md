## Introduction

In order to accommodate 2D effects we have modified how Segment settings are used and added 2D Matrix and panel variables on the [Led Preferences](https://github.com/atuline/WLED/wiki/LED-Preferences)settings.
Note: Currently only working in dev. Segment settings currently in SEGMENT2DV2 Branch of dev. You are invited to test this and give feedback on [Beta testing discord channel](https://discord.com/channels/700041398778331156/700701772838207640)

## 2D architecture

WLED SR distinguishes between the following levels
* 2D Segment (SEGMENT2DV2 Branch)
* 2D Matrix (dev)
* 2D Panel (dev)

## 2D Segments
As WLED supports multiple segments, all effects and therefore also 2D effects are first projected on a segment. In [1D](https://github.com/Aircoookie/WLED/wiki/Segments), a segment is a zone on a LED strip. 
In 2D, a segment is a rectangle on a 2D matrix.

