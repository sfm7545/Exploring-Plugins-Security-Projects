# Ghidra and IDA Pro: Exploring Plugins for Reverse Engineering
Ghidra and IDA Pro are reverse engineering tools which allow a malware analyst to view the assembly code of a binary.
Both programs have support for scripting and plugins, which help make malware analysis easier. 
The goal of this project is to demonstrate the functionality of Ghidra and IDA Pro, as well as the use of plugins and scripting.
## Using Ghidra
1. Ghidra must be installed, preferrably on a VM.
2. Open Ghidra.
3. Create a new project.

![Create a new project.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/GhidraE1.PNG "Create a new project.")

4. In order to analyze a binary, you must add the binary to the project. The easiest way to accomplish this is by dragging and dropping the file into the workspace.
5. Ghidra will then generate a summary of the file, showing information including the last modified date, the compiler, and more.

![Ghidra generates a summary of the file.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/ghidrae2.PNG "Ghidra generates a summary of the file.")

6. From here, select the code browser tool. You can select what you wish to analyze with the Analysis Options popup. 
7. The file will then be analyzed and the dashboard will launch. The dashboard initially shows the file in assembly. There are many items you can filter for, including:
* Strings
* Header info
* Imports and exports
* Functions
* Data Types

## Using IDA Pro
1. Open IDA.
2. Open a file you wish to analyze. 
3. IDA will then display the assembly code for the binary.

![IDA displaying assembly of a file.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/IDA1.PNG "IDA displaying assembly of a file.")

4. From here, you can search through each individual function.
5. You can also view imports/exports and the hex version of the code.
### Part 1: Plugins
## Decompilers 
Both Ghidra and IDA Pro have popular decompilers, which are used to convert assembly into readable C pseudocode. This makes it much easier to analyze the code of a malicious binary. 
### Ghidra's Decompiler 
-------
Ghidra's decompiler is built in.
1. Load a project.
2. Find dissasembled code of interest.
3. Double click function call, and Ghidra will automatically decompile it.
4. From there, you can analyze the C pseudocode. 

![Pseudocode generated in Ghidra.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/ghidracodesample.PNG "Pseudocode generated in Ghidra.")


### IDA's Decompiler
------
IDA uses a plugin for its decompiler, named Hex-Rays. 
1. Open a binary file with IDA.
2. Under the *Jump* tab, select *Jump to pseudocode*.

![Press "Jump to pseudocode"](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/IDA2redbox.PNG "Press "Jump to pseudocode"")

3. IDA will prompt and let you know that you will be using its cloud plugin decompiler.
4. Accept this, and the pseudocode C will be generated.

![Pseudocode generated in IDA.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/IDA3.PNG "Pseudocode generated in IDA.")


IDA's decompiler plugin is quick and easy to use, and generates a succinct, readable C pseudocode. 

--------
With this C pseudocode, it is much easier to understand what a program's functionality may be. An analyst can check each individual function of the program, and find out what the imports and exports are used for. Obfuscation will make this more difficult, of course, but it will be easier to tell if code is meaningless in the C pseudocode.

## GPTHidra

GPThidra is a script for Ghidra which integrates ChatGPT functionality. With GPTHidra installed, an analyst can select a function and use an API call to have ChatGPT describe what the pseudocode that was decompiled means. 
 #### Installing GPTHidra

 1. Copy the the python file data from [GPTHidra's Github.](https://github.com/evyatar9/GptHidra)
 2. Open any project in Ghidra.
 3. Open the "Window" tab and select *Script Manager*
 4. This will open Ghidra's Script Manager. Select the *New Script* button.
 5. Select *Python* as the language for the script.
 6. Paste the python file data into the new script and rename it GptHydra.py
 7. Make an OpenAI API key and past it into the API_KEY variable.
 8. Save this file.
 9. Now, when a binary file is open, select any function. Press Ctrl + Alt + G and GPTHidra will run. 
 10. It may fail if your OpenAI key is out of uses.

## Ghidra and IDA Pro Comparisons

Ghidra is a highly customizable open source reverse engineering software. However, its decompiler is less efficient than IDA Pro's.

IDA Pro has a fast decompiler with rather clear pseudocode, but is not a free program and is closed-source. 


## References

