# Custom effects

Custom effects are effects which are not hard coded in the WLED repository but specified by a file (program file).

The big advantage of this is that effects are not limited by what is made by WLED programmers but anybody can create effects without releasing a new version of WLED.

A disadvantage is that the file needs to be loaded, examined and then run in real time. This takes more time then coding it directly into the WLED code.

Another disadvantage is that this software is currently (November, 2021) 'experimental' meaning that it has just been released and is not finished by far. But, as it is open source, everybody can help to develop this further ;-)

# How it works

Program files are uploaded to the file system of WLED (/edit) and after selecting effect '⚙️ Custom Effect', the file is opened, it’s content is examined and executed. If you want to change the effect, you change the file and upload and run it again.

The program file contains structures like if statements, for loops, assignments, calls (e.g. renderFrame) etc., commands like setPixelcolor and variables like ledCount:

`program ColorRandom`

`{`

   `function renderFrame() {`

      `for (i = 0; i < ledCount; i = i + 1) {`

         `color = random()`

         `setPixelColor(i, color)`

      `}`

   `}`

`}`

More examples can be found [here](https://github.com/ewoudwijma/ARTI/tree/main/wled/Examples).

# User interface

As this is new functionality the existing WLED user interface is used without modifications. In the future changes can be made to make things easier. Currently, Custom effects are build in [WLED Soundreactive, latest dev version](https://github.com/atuline/WLED/tree/dev). See [here](https://github.com/MoonModules/WLED/wiki/Hardware#software) how to compile or install a precompiled bin.

The following steps are needed to run a Custom Effect:

* Upload files to /edit: The definition file wled.json and default.wled should be uploaded at minimal (you can find them [here](https://github.com/ewoudwijma/ARTI/tree/main/wled))

![Slash Edit](https://github.com/ewoudwijma/ARTI/blob/main/Images/SlashEditPNG.PNG?raw=true)

* Upload [presets.json](https://github.com/ewoudwijma/ARTI/tree/main/wled) to /edit to get presets for current examples pre loaded (change "stop" from 50 to the number of leds you have connected) (delete old presets.json in /edit first. Reboot to make them visible in the UI)
* Select one of the presets. Result should be visible on the led-strip

![Examples presets](https://github.com/ewoudwijma/ARTI/blob/main/Images/ExamplesPreset.PNG?raw=true)

To change or add effects:

* Select effect ‘⚙️ Custom Effect’ in the effects tab. The default effect (default.wled) will be executed if present in /edit.

![Custom effect](https://github.com/ewoudwijma/ARTI/blob/main/Images/CustomEffect.PNG?raw=true)

* Change a Custom Effect: Go to the Segments tab. The name of the segment defines the filename of the effect to run. the program file (without .wled) you want to run, if no name is given the default effect default(.wled) will be used 

![Segment name](https://github.com/ewoudwijma/ARTI/blob/main/Images/SegmentName.PNG?raw=true)

NOTE: Currently selecting Custom effects repeatedly will cause a crash / reboot. There must be a memory leak somewhere which has not been found yet... Therefore, above steps will not always work well. Alternatively edit / upload the presets.json file or edit API Commands directly, see [below](#preset-api-command):

![Preset](https://github.com/ewoudwijma/ARTI/blob/main/Images/Preset.PNG?raw=true)

# Current status

November 2021
* first release on WLED SR / dev branch
* Only 1 segment
* No sliders
* Crash if selected again
* Run only simple programs. As this tool is developed step by step, more complex programs can be run later.

# How it works in detail

The program file contains commands which adhere to a standard. These commands are specified in a definition file called [wled.json](https://github.com/ewoudwijma/ARTI/tree/main/wled). By this we can create and further develop our own WLED language.

To run this, a tool called Arduino Real Time Interpreter ([ARTI](https://github.com/ewoudwijma/ARTI)) is used. Actually this tool has been made to make Custom effects possible in WLED but can also be used without WLED. The tool is build using compiler technology and can support not only the WLED definition file but 'any' definition file. 

Arti will run the following steps sequentially: Lexer, Parser, Semantic Analyzer and Interpreter. The first 3 steps are done once if an affect is selected (SEGENV.call == 0). Interpreter will be executed one time to initialize global variables and functions and then run in a loop executing the function 'renderFrame'. [See fx.cpp in the ARTI Github repo](https://github.com/ewoudwijma/ARTI/tree/main/wled).

Another definition file can be created if you want to run commands in another coding language. In the Arti Github repository, pas.json is added as a demo to show an example of another definition file. See [below](#definition-files) how to create another definition file.

# More
* Currently this has been added in the WLED Soundreactive / dev branch. As this is not limited to the Soundreactive fork, it could also be added to it's upstream repo: WLED AC. This might be a future step. At this moment, Custom effects do not support Soundreactive specific functions (it supports hardly anything at all ;-) ). It probably will support it in the future. Real time constraints for sound require some performance tuning to be done first.

# Preset API command

To create a new custom effect, insert the following API command in a new preset and replace "ColorFade" with the prefix of the filename of the Custom Effect (In this example the filename is ColorFade.wled)

{"on":true,"bri":128,"transition":7,"mainseg":0,"seg":[{"id":0,"start":0,"stop":30,"grp":1,"spc":0,"of":0,"on":true,"bri":255,"n":"ColorFade","col":[[255,160,0],[0,0,0],[0,0,0]], "fx":187,"sx":128,"ix":128,"f1x":128,"f2x":128,"f3x":128,"pal":0,"sel":true,"rev":false,"rev2D":false,"mi":false,"rot2D":false},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0},{"stop":0}]}

(fx:187 is id of the Custom Effect)

# Contribute to further development

## Run on Windows
* Clone the ARTI repository
* Run on Windows using CompileAndRunGCC.bat
* Set the right effect in arti_test.cpp e.g. default.wled
* Check created parsetree and log file e.g. default.wled.json and default.wled.log
* Can run on Mac/Linux if CompileAndRunGCC.sh is created

## Deploy on windows
* Use Visual Studio
* Open the repo folder
* Modify code
* Run on windows using CompileAndRunGCC.sh

## Deploy on Arduino
* Use Visual Studio
* Download latest [WLED SR dev repository](https://github.com/atuline/WLED/tree/dev)
* Copy your arti.h / arti_wled_plugin.h to the repository (wled00/src/dependencies/arti). Upload your wled.json or <effect>.wled to /edit
* Build on arduino. See [link](https://github.com/MoonModules/WLED/wiki/Hardware#software).

## Contribute
* Submit a pull request from your clone to the upstream ARTI repository

# Definition files
Definition files define the syntax and semantics of the programming language you want to use. ARTI supports 'any' language as long as it has functions, calls, variables, for, if etc. ... [wled.json](https://github.com/ewoudwijma/ARTI/tree/main/wled)) is an example of this. Any new definition file should contain the following parts:

`{`
  `"meta": {"version": "0.0.4", "start":"program"},`
  `"program": ["PROGRAM","ID","block"],`
  `"block": ...,`

  `"TOKENS":`
  `{`
    `"ID": "ID",`
    `"INTEGER_CONST": "INTEGER_CONST",`
    `"REAL_CONST": "REAL_CONST",`
    `"PROGRAM": "PROGRAM",`
  `},`

  `"SEMANTICS":`
  `{`
    `"program": {"id":"Program", "name":"ID", "block": "block"},`
    `"variable": {"id":"Var", "name":"ID", "type": "type"},`
    `"assign": {"id":"Assign", "name":"varleft", "indices":"indices", "value":"expr"},`
    `"function": {"id":"Function", "name":"ID", "formals": "formals", "block": "block"},`
    `"formal": {"id":"Formal", "name":"ID", "type": "type"},`
    `"call": {"id":"Call", "name":"ID", "actuals": "actuals"},`
    `"for": {"id":"For", "from":"assign", "condition":"expr", "increment": "increment", "block":"block"},`
    `"if": {"id":"If", "condition":"expr", "true":"block", "false": "elseBlock"},`
    `"expr": {"id":"Expr"},`
    `"term": {"id":"Term"},`
    `"varref": {"id":"VarRef", "name":"ID"}`
  `},`

  `"EXTERNALS":`
  `{`
    `"setPixelColor": {"pixelNr":"int", "color":"int"},`
    `"printf": {"args": "__VA_ARGS__"},`
    `"ledCount": {}`
  `}`

`}`

* a meta tag containing version and start, current version of arti.h requires minimal version 0.0.4. Start is the first part of your program. A program is specified by [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form)-like statements in the form of "symbol": "expression". Expression can contain special directives: ? is optional, + is one or more, * is 0 or more.
* SEMANTICS: tells arti how to recognize different parts of the syntax
* EXTERNALS: define predefined functions and variables. They should be defined in arti_<definition>_plugin.h
* For any new definition, arti.h should have an include statement of the plugin file