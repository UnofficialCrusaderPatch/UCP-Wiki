# Finding Values with Cheat Engine

This guide explains how to use Cheat Engine, a memory scanner and debugger, to find the memory addresses of game values like gold, resources, or unit health. This is an essential first step for many modding tasks.

> **TODO:** This guide needs to be written by someone familiar with Cheat Engine. It should include clear, step-by-step instructions with screenshots.

## Guide Outline

1.  **Setting up Cheat Engine:**
    > **TODO:** Explain how to download and install Cheat Engine and attach it to the `Stronghold Crusader.exe` process.
2.  **Finding a Simple Value (Your Gold):**
    > **TODO:** Provide a beginner-friendly tutorial on finding the address for your gold. Explain the process of scanning, changing the value in-game, and then scanning again for the new value.
3.  **Finding Unknown or Complex Values:**
    > **TODO:** Explain how to use "Unknown initial value" and subsequent "Increased value" / "Decreased value" scans to find values like unit HP.
4.  **Using Pointer Scans for Stable Addresses:**
    > **TODO:** Explain why many addresses change each time the game is launched. Introduce the concept of pointers and walk through a pointer scan to find a stable "base address" that can be reliably used for patching.
5.  **Finding What Code Accesses an Address:**
    > **TODO:** Show how to use Cheat Engine's "Find out what writes to this address" feature to pinpoint the exact assembly instruction responsible for changing a value (e.g., the code that subtracts gold when you buy something). This is invaluable for reverse engineering.