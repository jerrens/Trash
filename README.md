<!-- markdownlint-configure-file {
    "no-inline-html": {
        "allowed_elements": [ "div" ]
    },
    "no-multiple-blanks": {
        "maximum": 4
    }
}
-->

# Trash Management

This script provides an alternative to permanently deleting files by moving them to a "trash" or "recycle" directory, where they can be reviewed, restored, or purged at a later time.
It allows management of files in the trash directory through various commands, offering enhanced control over accidental deletions and organized file removal.

## Features

- **Move to Trash**: Moves specified files or directories to a designated trash directory instead of deleting them permanently.
- **Listing Trash Contents**: Lists files in the trash, with the option to filter files by age (default: older than 7 days).
- **Purge Old Files**: Deletes files from the trash that are older than a specified number of days.
- **Dry Run Mode**: Displays command(s) that would be executed without making any actual changes.


### In the future

- **Restore Functionality**: (Concept) Allows for restoring files to their original paths.
- **Compression Support**: (Concept) Compresses trash contents, supporting background execution and safe handling of active files.


## Default Settings

- **Trash Directory Path**: Default paths include `$XDG_DATA_HOME/Trash` or a custom `~/.recycle-bin` if no XDG directory is found.
- **Default Age for Purge/List**: 7 days
- **Verbose Level**: 0 (adjustable via args)
- **Dry Run**: Disabled by default


## Usage

```bash
trash  [command] [options] <path>...
```


## Commands

- **list [age]**: Lists files in the trash that are older than the specified `age` (in days).
  - **Default age**: 7 days
  - Example: `./trash_management_script.sh list 5`
- **purge [age]**: Permanently deletes files from the trash that are older than the specified `age`.
  - Example: `./trash_management_script.sh purge 10`
- **dir**: Outputs the current trash directory path.
  - Example: `./trash_management_script.sh dir`
- **help**: Displays help information.
  - Example: `./trash_management_script.sh help`
- **version**: Displays the script version.
  - Example: `./trash_management_script.sh version`
- **<path>**: Moves the specified file(s) or directory(s) to the trash.
  - Example: `./trash_management_script.sh path/to/file1 path/to/file2`


## Options

These are set within the `trash` script itself and not normally edited by users.
At some point in the future, they may be properly exposed via a config file or environment variables

- **FILE_DELIM**: Delimiter used for naming trashed files (default: `___TRASHED_ON__`).
- **DEFAULT_AGE**: Default number of days for the purge and list commands (default: 7).
- **VERBOSE**: Controls logging output (higher values show more details).


## Examples

1. Move files to trash:

    ```bash
    ./trash_management_script.sh path/to/file1 path/to/file2
    ```

1. List files older than 5 days in the trash:

    ```bash
    ./trash_management_script.sh list 5
    ```

1. Purge files older than 10 days:

    ```bash
    ./trash_management_script.sh purge 10
    ```

1. Check trash directory path:

    ```bash
    ./trash_management_script.sh dir
    ```
