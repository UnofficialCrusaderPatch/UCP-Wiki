# Reverse Engineering with Ghidra

This is an advanced tutorial for developers who want to analyze the `Stronghold Crusader.exe` executable to find new functions to patch or to understand existing game logic.

**Warning:** This is a highly technical topic that requires a basic understanding of computer architecture and assembly language.

> **TODO:** This tutorial needs to be written by an expert modder from the community. It should be a step-by-step guide.

## Guide Outline

1.  **Setting up Ghidra:**
    > **TODO:** Explain how to download Ghidra and the required Java Development Kit (JDK).
2.  **Creating a Project and Importing the Executable:**
    > **TODO:** Walk through creating a new Ghidra project and importing `Stronghold Crusader.exe`. Detail the recommended analysis options to select.
3.  **Navigating the Ghidra Interface:**
    > **TODO:** Explain the key windows: Listing (assembly), Decompiler (pseudo-C code), Symbol Tree, and Data Type Manager.
4.  **Finding Key Functions:**
    > **TODO:** Provide techniques for finding important game functions, such as searching for known strings ("Not enough wood!") or identifying functions that access known memory structures (like the player data structure).
5.  **Analyzing and Understanding Game Logic:**
    > **TODO:** Show an example of analyzing a simple function, like the one that calculates damage, explaining how to read the decompiled code and cross-reference it with the assembly.