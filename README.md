# Ghidra and IDA Pro: Exploring Plugins for Reverse Engineering
Ghidra and IDA Pro are reverse engineering tools which allow a malware analyst to view the assembly code of a binary.
Both programs have support for scripting and plugins, which help make malware analysis easier. 
The goal of this project is to demonstrate the functionality of Ghidra and IDA Pro, as well as the use of plugins and scripting.

## Sections:
1) Part 1
2) Part 2


---


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

![Press 'Jump to pseudocode'](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/IDA2redbox.PNG "Press 'Jump to pseudocode'.")

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

![Select Script Manager](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/gptGhidra1.PNG "Script Manager is towards the bottom.")

 4. This will open Ghidra's Script Manager. Select the *New Script* button.

![Ghidra's Script Manager](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/gptghidra2.PNG "Ghidra's Script Manager.")

 5. Select *Python* as the language for the script.
 6. Paste the python file data into the new script and rename it GptHydra.py
 7. Make an OpenAI API key and past it into the API_KEY variable.

![Python file pasted.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/gptghidra5.PNG "Python file pasted.")

*Note: the API key shown in this screenshot will not work.*

 8. Save this file.
 9. Now, when a binary file is open, select any function. Press Ctrl + Alt + G and GPTHidra will run. 

![GPTHidra in action.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/gptghidra7.PNG "GPTHidra in action.")

 10. It may fail if your OpenAI key is out of uses.

## Ghidra and IDA Pro Comparisons

Ghidra is a highly customizable open source reverse engineering software. However, its decompiler is less efficient than IDA Pro's.

IDA Pro has a fast decompiler with rather clear pseudocode, but is not a free program and is closed-source. 


## References

* ["Getting Started With Ghidra For Malware Analysis"](https://www.youtube.com/watch?v=dW8YFRX2BGk&t=148s)

* ["Reverse Engineering Tutorial with IDA Pro – An Introduction to IDA Pro."](https://www.youtube.com/watch?v=N_3AGB9Vf9E)

* ["Awesome IDA, Ghidra, x64DBG, GDB & OllyDBG plugins"](https://github.com/fr0gger/awesome-ida-x64-olly-plugin/blob/master/README.md#IDA-Plugins)

# Part 2
In this part, we focused on plugins for Ghidra from a research perspective.
We wished to discover plugins that help make malware analysis simpler, and potentially automate it.

A focus of this project is the use of AI, in which machine learning or large language models could be leveraged to make reverse engineering easier. 

---
#### Ghidra's Python Interpreter
This technique allows for the automation of function mapping, which could quickly gather details like
1) function names
2) address
3) sizes

which help reduce the workload during analysis.
With the use of AI models, patterns in the code, as well as obfuscation can be detected.


![Ghidra Python Interpreter](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/pythoninterpreter.png "Python Interpreter")


---
#### machinelearning
Machinelearning is a plugin developed by Ghidra that can be installed from the toolbox menu.

This plugin allows for the training of large language models natively in Ghidra.

As opposed to training off of thousands of samples, machinelearning allows you to train a small language model using the file you are currently working on.

![Installing machinelearning](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/installingML.PNG "Installing machinelearning")


---
#### IDA Pro's Debugger
The debugger built into IDA Pro allows for realtime monitoring of malware.

While it is built as a debugger, a user can run a program instruction by instruction and determine functionality, including memory changes and other interactions that may not be seen through just static viewing of the code. 

![IDA Pro Debugger](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/idadebugger.png "IDA Pro Debugger")

---
#### Call Graph
Ghidra's function call graph creates a visual of function relationships. It can help find openings in the code, or obfuscated/complicated sections.

![Function Call Graph](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/callgraph.png "Function Call Graph")

---

## Experiment: GPTHidra Revisited
* Tools used: Ghidra, GPTHidra script.


Previously, we discussed GPTHidra and how to install it. However, to prove how it works and that it is an effective tool for automation, we conducted an experiment using a crackme file.

The crackme file is a relatively simple program, which requests a password to activate it. The password, however, is unknown. 


![crackme file when run](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/crackmepasswordrequest.PNG "crackme file when run")


If GPTHidra can determine a valid password for this file, then we can continue our analysis much faster.

To achieve this, we must:

1) Open the crackme file in Ghidra and analyze it.
2) Find the main function. Check the exports.
3) There is a function there named __mainCRTStartup. This function is used on startup.
4) This function calls another function, which we double click and find the actual main function inside. 

![Finding main.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/findingmain.PNG "Finding main.")

5) We can double click _main and find the main function.
6) From here, we call the GPTHidra script to tell us what we are looking at.

![GPTHidra's Analysis.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/ghidraGPTusing1.PNG "GPTHidra's Analysis")

7) The output of ChatGPT appears in the console.
8) It tells us that this function asks for a user input and calls another function to check that user input.
9) We can now check this function.
10) Call the GPTHidra script in the check function. 

![GPTHidra's Analysis.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/ghptGPTsing.PNG "GPTHidra's Analysis.")

11) GPTHidra is able to determine the function being performed to get the correct password.
12) It determined that a password just needs to add up to 15 to be considered valid, and recommends the password "555".
13) Let's try 555 as a password for the crackme file.

![555 is a valid password.](https://github.com/sfm7545/Exploring-Plugins-Security-Projects/blob/main/screenshots/crackmepasswordOK.PNG "555 is a valid password.")

GPTHidra is an excellent example of how artificial intelligence can enhance the reverse engineering experience.




