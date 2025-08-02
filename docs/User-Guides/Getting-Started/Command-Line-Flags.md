# Command-Line Flags

The UCP framework extends Stronghold Crusader's built-in command-line options with several new flags for customization and debugging. You can use these flags when launching the game executable from a command prompt or by setting launch options in clients like Steam.

## UCP Command-Line Flags

* `--ucp-console`
    * Enables the UCP's developer console window. This is disabled by default in standard builds.

* `--ucp-no-console`
    * Forces the console to be hidden. This is useful if you are running a Developer build, where the console appears by default.

* `--ucp-verbosity <level>`
    * Sets the logging verbosity for the UCP log file (`ucp_log.txt`).
    * **Levels:**
        * `0`: Info (default)
        * `1`: Debug
        * `2`: Verbose

* `--ucp-console-verbosity <level>`
    * Sets the logging verbosity for the console window, if enabled. Uses the same levels as `--ucp-verbosity`.

* `--ucp-game-data-path <path>`
    * Sets a custom folder path to load and save user data like game settings, progress, maps, and save files.

* `--ucp-no-security`
    * Disables security features, permitting non-verified modules to be loaded. This is the default behavior in a Developer build.

* `--ucp-security`
    * Forces security features to be enabled. Mainly for development and testing purposes.

### Example Usage

To launch the game with the console enabled at the highest verbosity and with security disabled, you would run the following command from your game directory:

```cmd
"Stronghold Crusader.exe" --ucp-console --ucp-console-verbosity 2 --ucp-no-security
```