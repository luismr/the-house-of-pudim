# How to Configure iTerm2 on macOS for a Beautiful and Productive Terminal

If you're a macOS user and spend a lot of time in the terminal, configuring iTerm2 can significantly enhance your development experience. In this guide, we'll go through the steps to set up iTerm2 with a sleek design, useful plugins, and themes to make your terminal both visually appealing and efficient.

### Assumptions

To keep things simple and effective, we are following these principles:

- **KISS (Keep It Simple, Stupid) principle** – Simplicity is key for efficiency and maintainability.
- **Operating System: macOS** – This guide is specifically for macOS users. Some steps may need adjustments for other operating systems.
- **Fresh macOS install** – We assume the setup is being done on a fresh macOS installation. If you already have a custom environment, you may need to adapt the steps accordingly.
- **Preferred Editor: vi** – This guide uses `vi` as the terminal editor, but you can use any editor of your choice, such as `nano` or `vim`.
- **Easy setup** – No complex installation steps or configurations.
- **Minimal effort** – The guide avoids unnecessary steps and focuses on what matters.

## 1. Install iTerm2

First, we need to install iTerm2, which offers more features and customization options compared to the default macOS Terminal.

### Install Homebrew (if not installed)

**What is Homebrew?** Homebrew (or Brew) is a package manager for macOS that simplifies the installation of software. It allows developers to install, update, and manage packages and applications efficiently using the command line.

**Why is Homebrew good for business?**

- **Streamlined Software Management** – Businesses can easily install and maintain essential development tools.
- **Automation & Scripting** – Enables automation of software installations, improving workflow efficiency.
- **Security & Updates** – Keeps software up to date with the latest patches and security updates.
- **Open Source & Community-Driven** – Actively maintained by a large community, ensuring reliable and up-to-date packages.

To install Homebrew, run:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Install iTerm2

```sh
brew install --cask iterm2
```

## 2. Install Zsh

Zsh (Z Shell) is an improved shell that offers advanced features and customization. It is faster, more powerful, and comes with better scripting capabilities than the default Bash shell on macOS. Keeping Zsh updated ensures that you have the latest security patches and performance improvements, making it an excellent choice for developers and businesses that require a reliable and efficient shell environment.

### Install Zsh

```sh
brew install zsh
```

## 3. Install Oh My Zsh

Oh My Zsh is an open-source framework for managing Zsh configurations. It simplifies customization, enhances productivity, and brings a collection of powerful plugins and themes to your terminal setup.

### Why Use Oh My Zsh?
- **Customization:** Comes with over 300 themes and an extensive collection of plugins.
- **Productivity Boost:** Offers features like auto-suggestions, syntax highlighting, and tab completion.
- **Plugin System:** Enables integration with Git, Docker, Node.js, Python, and more.
- **Alias Support:** Provides useful command shortcuts to speed up workflow.
- **Community-Driven:** Maintained by an active open-source community with frequent updates.

### Install Oh My Zsh

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 4. Customize iTerm2 with Material Design Colors

To make iTerm2 visually appealing, we’ll use Material Design Colors.

### Download Material Design Color Scheme

```sh
cd ~/Downloads
curl -O https://raw.githubusercontent.com/MartinSeeler/iterm2-material-design/master/material-design-colors.itermcolors
```

### Apply the Color Scheme in iTerm2

1. Open **iTerm2**.
2. Navigate to **iTerm2 > Preferences > Profiles > Colors Tab**.
3. Click **Color Presets…** at the bottom right.
4. Click **Import…** and select the `material-design-colors.itermcolors` file.
5. From **Load Presets…**, select **material-design-colors**.

## 5. Enable Plugins for Better Development Workflow

Oh My Zsh comes with many useful plugins. To enable them, follow these steps:

1. Open a terminal window.
2. Edit the **.zshrc** file by running:
   ```sh
   vi ~/.zshrc
   ```
3. Locate the **plugins** line and update it as follows:
   ```sh
   plugins=(git docker mvn pip pipenv npm nvm macos vscode zsh-autosuggestions zsh-syntax-highlighting web-search)
   ```
4. Save the file (`ESC`, then type `:wq` and press `Enter`).
5. Apply the changes:
   ```sh
   source ~/.zshrc
   ```

### Explanation of Each Plugin:
- **git** – Provides aliases and functions for working with Git repositories.
- **docker** – Adds helpful aliases and functions for managing Docker containers and images.
- **mvn** – Simplifies commands for working with Apache Maven, commonly used in Java development.
- **pip** – Enhances Python's package management system by providing aliases for `pip`.
- **pipenv** – Helps manage Python virtual environments and dependencies easily with Pipenv.
- **npm** – Provides helpful aliases and functions for managing Node.js packages with npm.
- **nvm** – Enables seamless Node.js version management using Node Version Manager (NVM).
- **macos** – Includes useful macOS-specific commands for improving system management.
- **vscode** – Allows launching Visual Studio Code directly from the terminal with the `code` command.
- **zsh-autosuggestions** – Suggests commands based on history as you type, improving workflow speed.
- **zsh-syntax-highlighting** – Highlights command syntax to help catch errors before execution.
- **web-search** – Enables quick web searches directly from the terminal using pre-defined search engines.

Alternatively, run the following script to execute these steps automatically:

```sh
sed -i '' 's/^plugins=(.*)/plugins=(git docker mvn pip pipenv npm nvm macos vscode zsh-autosuggestions zsh-syntax-highlighting web-search)/' ~/.zshrc
source ~/.zshrc
```

## 6. Change the Theme to an Emoji-based Theme

If you like a fun and unique look, try an emoji-based theme. Follow these steps:

```sh
cd ~/Downloads
git clone https://github.com/meiokubo-zz/emoji.zsh-theme
cp ~/Downloads/emoji.zsh-theme/emoji.zsh-theme ~/.oh-my-zsh/themes/
vi ~/.zshrc
```

Modify the **ZSH_THEME** line to:

```sh
ZSH_THEME="emoji"
```

Then apply the changes:

```sh
source ~/.zshrc
```

## 7. Enable Native macOS Shortcut Keys in iTerm2

Follow the instructions in **iTerm2 > Preferences > Profiles > Keys Tab**, and load the **Terminal.app Compatibility** preset.

### Customize Keybindings for Navigation

If keybindings for **Command + Left Arrow** and **Command + Right Arrow** are not working as expected, you can manually configure them:

1. Open **iTerm2**.
2. Navigate to **iTerm2 > Preferences > Profiles > Keys Tab**.
3. Click the **+** button to add a new shortcut.
4. Set the **Keyboard Shortcut** to `Command + Left Arrow`.
5. Under **Action**, select **Send Hex Code** and enter `0x01` (moves to the beginning of the command line).
6. Repeat the process for `Command + Right Arrow`, setting the hex code to `0x05` (moves to the end of the command line).

### Additional Keybindings
- **Move one word backward**: `Option + Left Arrow` → Send Hex Code `0x33b`
- **Move one word forward**: `Option + Right Arrow` → Send Hex Code `0x33f`

Close Preferences and test the shortcuts in your terminal to ensure they are working as expected.

Follow the instructions in **iTerm2 > Preferences > Profiles > Keys Tab**, and load the **Terminal.app Compatibility** preset.

## Conclusion

With this setup, you now have a well-configured and visually appealing iTerm2 terminal with enhanced functionality. You can further customize your terminal with different themes and plugins by exploring the **Oh My Zsh** framework.

Enjoy your new and improved terminal experience on macOS!
