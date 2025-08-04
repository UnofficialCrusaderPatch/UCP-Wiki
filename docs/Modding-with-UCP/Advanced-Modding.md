# Advanced Modding

This section is for modders who want to go beyond content creation and delve into the code of Stronghold Crusader itself. The techniques described here are powerful but require technical expertise. They are the foundation upon which new code-altering **Modules** are built.

The primary goal of advanced modding is to analyze the game's executable to discover how it works, find memory addresses or functions to modify, and ultimately add new scripted logic to the game.

---

## Techniques & Tutorials

* **[Finding Values with Cheat Engine](./Advanced-Modding/Finding-Values-Cheat-Engine.md)**
    * An essential first step in reverse engineering. This guide outlines how to use Cheat Engine to scan the game's memory to find values like gold, resources, or unit health, and how to trace what code accesses them.

* **[Reverse Engineering with Ghidra](./Advanced-Modding/Reverse-Engineering-Ghidra.md)**
    * A deep-dive tutorial on using Ghidra, a professional-grade disassembler and decompiler, to analyze `Stronghold Crusader.exe`. Learn how to navigate the game's code, identify key functions, and understand the logic that powers the game.