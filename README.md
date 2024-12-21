
# Script Documentation: Bash Installer Script

## Overview
This Bash script is designed to automate system setup, validate environments,
install required packages, and perform system-specific configurations. It includes
robust error handling, detailed logging, and compatibility checks.

---

## Features
- **Error Handling**: Captures and reports unexpected errors using a `trap` mechanism.
- **Environment Validation**: Verifies dependencies, system configurations, and compatibility.
- **Logging Framework**: Logs messages with configurable levels (DEBUG, INFO, WARNING, ERROR, CRITICAL).
- **Git Integration**: Retrieves repository metadata like branch, tags, and commit details.
- **Interactive Installer**: Supports guided installation and configuration tasks.
- **Dynamic Debugging**: Provides optional debug output for detailed logs.
- **Flexible Arguments**: Allows customization through command-line options.
- **Compatibility**: Ensures compatibility with supported Raspberry Pi models and OS versions.

---

## Usage
\`\`\`bash
./install.sh [options]
\`\`\`

### Command-line Options
| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| \`--dry-run\` \`-dr\`       | Enable dry-run mode (no actions performed).                                |
| \`--version\` \`-v\`        | Display the script version and exit.                                       |
| \`--help\` \`-h\`           | Show this help message and exit.                                           |
| \`--log-file <path>\`     | Specify the log file location.                                             |
| \`--log-level <level>\`   | Set the logging verbosity level (DEBUG, INFO, WARNING, ERROR, CRITICAL).   |
| \`--terse <true/false>\`  | Enable or disable terse output mode.                                       |
| \`--log-console <value>\` | Enable or disable console logging (\`true\` or \`false\`).                     |

---

## Script Functions

### Core Functions
- **\`main\`**: The entry point for the script. Executes initialization, validation, and installer tasks in sequence.
- **\`start_script\`**: Displays a welcome message and prompts the user to continue or quit.

### Logging
- **\`setup_log\`**: Configures the logging framework, including file paths and verbosity levels.
- **\`log_message\`**: Logs messages to console and/or file based on the configured log level and output mode.
- **\`toggle_console_log\`**: Toggles console logging on or off.

### Error Handling
- **\`trap_error\`**: Captures unexpected errors during execution and logs the context.
- **\`die\`**: Logs a critical error and terminates the script with a specified exit code.

### Environment Validation
- **\`check_bash\`**: Ensures the script is executed in a Bash shell.
- **\`check_sh_ver\`**: Validates that the Bash version meets the minimum requirement.
- **\`check_bitness\`**: Verifies system architecture compatibility.
- **\`check_release\`**: Ensures the OS version is within the supported range.
- **\`check_arch\`**: Checks if the Raspberry Pi model is supported.
- **\`check_internet\`**: Validates internet connectivity with optional proxy settings.
- **\`validate_depends\`**: Ensures required dependencies are installed.
- **\`validate_env_vars\`**: Checks for the presence of required environment variables.

### Git Integration
- **\`get_repo_org\`**: Retrieves the Git repository organization name.
- **\`get_repo_name\`**: Fetches the repository name from the Git configuration.
- **\`get_git_branch\`**: Retrieves the current Git branch or the source of a detached HEAD.
- **\`get_last_tag\`**: Returns the latest Git tag.
- **\`get_sem_ver\`**: Generates a semantic version string based on repository state.

### Installer Functions
- **\`apt_packages\`**: Installs or upgrades packages listed in the global \`APTPACKAGES\` array.
- **\`set_time\`**: Configures the system timezone interactively.

### Utility Functions
- **\`add_dot\`**: Adds a leading dot to a string if missing.
- **\`remove_dot\`**: Removes a leading dot from a string if present.
- **\`add_slash\`**: Appends a trailing slash to a string if missing.
- **\`remove_slash\`**: Removes a trailing slash from a string if present.

---

## Global Variables
### Configuration Variables
- **\`THIS_SCRIPT\`**: Name of the script being executed.
- **\`REPO_ORG\`**: Organization or owner of the Git repository.
- **\`REPO_NAME\`**: Name of the Git repository.
- **\`SEM_VER\`**: Semantic version of the script, generated dynamically.
- **\`LOG_LEVEL\`**: Logging verbosity level.
- **\`LOG_OUTPUT\`**: Controls where logs are written (file, console, both).
- **\`APTPACKAGES\`**: Array of required APT packages for installation.

### Environment Variables
- **\`REQUIRE_SUDO\`**: Indicates if root privileges are required.
- **\`REQUIRE_INTERNET\`**: Flags whether internet connectivity is mandatory.
- **\`MIN_BASH_VERSION\`**: Specifies the minimum supported Bash version.
- **\`SUPPORTED_MODELS\`**: Associative array of supported Raspberry Pi models.
- **\`SUPPORTED_BITNESS\`**: Defines the supported system architecture.

---

## Dependencies
The following system utilities and packages are required:
- **System Utilities**: \`awk\`, \`grep\`, \`tput\`, \`curl\`, \`wget\`, \`git\`
- **APT Packages**: \`apache2\`, \`php\`, \`jq\`, \`libraspberrypi-dev\`, \`raspberrypi-kernel-headers\`

---

## Error Codes
| Code | Description                                |
|------|--------------------------------------------|
| 0    | Successful execution.                      |
| 1    | Generic error or invalid input.            |
| 99   | Unknown or unexpected error.               |

---

## How to Contribute
To contribute:
1. Clone the repository and create a new branch for your changes.
2. Test your modifications thoroughly on supported systems.
3. Submit a pull request with detailed explanations of your changes.

---

## License
This script is open-source and distributed under the MIT License. See the \`LICENSE\` file for details.

---
