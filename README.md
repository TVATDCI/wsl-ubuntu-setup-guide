# **Complete Guide: Setting Up WSL, Ubuntu, and Zsh in VS Code**

## **1. Install Windows Subsystem for Linux (WSL) and Ubuntu**

### **Enable WSL and Virtual Machine Platform**

1. Open **PowerShell as Administrator** and run:
   ```powershell
   wsl --install
   ```
2. Restart your computer if prompted.

### **Install Ubuntu**

1. Open **PowerShell** and install Ubuntu:
   ```powershell
   wsl --install -d Ubuntu
   ```
2. Once installed, search for **Ubuntu** in the Start Menu and open it.
3. Set up your **UNIX username** and **password** (this is different from your Windows account).

---

## **2. Update Ubuntu and Install Essential Packages**

After opening Ubuntu, update and upgrade packages:

```bash
sudo apt update && sudo apt upgrade -y
```

Install essential tools:

```bash
sudo apt install -y curl git zsh wget
```

---

## **3. Install and Set Up Zsh with Oh My Zsh**

### **Install Oh My Zsh**

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Press **Y** when asked to change your default shell.

### **Install Plugins for Zsh**

Enhance your Zsh experience with the following plugins:

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Edit the Zsh configuration file:

```bash
nano ~/.zshrc
```

Find the `plugins=` line and modify it:

```bash
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```

Save and exit (**Ctrl + X**, then **Y**, then **Enter**), then apply the changes:

```bash
source ~/.zshrc
```

---

## **4. Install Powerlevel10k for a Beautiful Terminal**

### **Download Powerlevel10k Theme**

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

### **Set Powerlevel10k as the Default Theme**

1. Open the Zsh configuration file:
   ```bash
   nano ~/.zshrc
   ```
2. Find the line:
   ```bash
   ZSH_THEME="robbyrussell"
   ```
   Replace it with:
   ```bash
   ZSH_THEME="powerlevel10k/powerlevel10k"
   ```
3. Save and exit.
4. Apply changes:
   ```bash
   source ~/.zshrc
   ```
5. Restart your terminal to begin **Powerlevel10k configuration** and follow the prompts.

---

## **5. Install Neovim for an Improved Terminal Editor**

### **Install Neovim**

```bash
sudo apt install -y neovim
```

### **Set Neovim as the Default Editor**

```bash
echo "export EDITOR=nvim" >> ~/.zshrc
source ~/.zshrc
```

### **Enhance Neovim with Plugins**

1. Install **vim-plug** (plugin manager for Neovim):
   ```bash
   curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
   ```
2. Open Neovim and edit the config file:
   ```bash
   nvim ~/.config/nvim/init.vim
   ```
3. Add the following basic plugin setup:

   ```vim
   call plug#begin()
   Plug 'morhetz/gruvbox'
   Plug 'tpope/vim-sensible'
   Plug 'junegunn/fzf.vim'
   call plug#end()

   syntax on
   colorscheme gruvbox
   set number
   ```

4. Save and exit **(Esc, then type `:wq`)**.
5. Install the plugins inside Neovim:
   ```vim
   :PlugInstall
   ```
6. Restart Neovim for changes to take effect.

---

## **6. Sync VS Code Extensions Between Windows and WSL**

To use the same extensions in both environments:

1. Open **VS Code on Windows**.
2. Sign in to your **GitHub or Microsoft account** to enable **Settings Sync**.
3. Open **VS Code inside WSL** using:
   ```bash
   <<<<<<<<< Temporary merge branch 1
   =========
   git config --global user.name "YourName"
   git config --global user.email "youremail@example.com"
   ```
4. Check if Git is installed:
   ```bash
   git --version
   ```
5. Clone a GitHub repository:
   ```bash
   git clone https://github.com/yourusername/yourrepository.git
   ```

---

## **8. Useful Commands to Test Your Setup**

- **Check Ubuntu version:**
  ```bash
  lsb_release -a
  ```
- **List files in home directory:**
  ```bash
  ls -la ~
  ```
- **Check installed Node.js version:**
  ```bash
  node -v
  ```
- **Display system info using Neofetch:**
  ```bash
  sudo apt install -y neofetch
  neofetch
  ```

---

## **9. Accessing Ubuntu Files from Windows**

Your Ubuntu files are stored inside WSL. You can access them in **Windows File Explorer** by typing:

```plaintext
\\wsl.localhost\Ubuntu\home\<your-UNIX-username>
```

Or navigate to:

```plaintext
C:\Users\YourWindowsUsername\AppData\Local\Packages\CanonicalGroupLimited...\LocalState\rootfs\home\<your-UNIX-username>
```

---

## **10. Moving Old Projects to WSL**

1. Move your old project folders to:
   ```plaintext
   /home/<your-ubuntu-username>/
   ```
2. Open **VS Code** and navigate to the folder inside WSL.
3. Run it in **Ubuntu terminal** using:

   ```bash
   cd ~/your-project-folder
   >>>>>>>>> Temporary merge branch 2
   code .
   ```

4. Sign in again and **enable syncing**.
5. Your extensions and settings should now be synced!

---

## **7. Difference Between Zsh and Neovim**

- **Zsh** is an interactive shell for running commands, while **Neovim** is a powerful text editor.
- **Zsh** helps with command-line efficiency, auto-suggestions, and plugins.
- **Neovim** is optimized for coding, with syntax highlighting, plugins, and customization.
- **Using Both:** You can configure **Neovim as your Zsh editor** by setting:
  ```bash
  export EDITOR=nvim
  ```
  This allows you to edit files inside your terminal seamlessly.

**Pros:**
✅ Neovim as default editor in Zsh streamlines workflow.
✅ Zsh enhances command-line experience.

```plaintext
C:\Users\YourWindowsUsername\AppData\Local\Packages\CanonicalGroupLimited...\LocalState\rootfs\home\<your-UNIX-username>
```

=======
**Cons:**
❌ Using both might be overwhelming for beginners.
❌ Requires time to configure properly.

---

✅ **Now you have the perfect dual-terminal setup: Windows for daily tasks & Ubuntu for development!** 🚀

## Ps.

Since I have been often using multiple terminal tabs for your full-stack development, tmux is a great addition. Here’s why: It is part of my learning experiences of things are 😁

### Split Your Terminal Efficiently

You can divide your terminal into multiple panes and navigate between them easily.
Example use case: Have backend logs on one side and your frontend dev server on another.

### Persistent Sessions

If you close your terminal by mistake, your running processes (like servers, databases, etc.) won’t die! You can reattach to them.

### Better Navigation & Productivity

You don’t have to constantly open and close new terminal tabs.
Instead, just split panes inside tmux and jump between them with key bindings.

Since you already have Zsh + Oh My Zsh + Powerlevel10k, I’d add tmux and configure it to work seamlessly with your current setup.

1️⃣ **Install tmux**

```sh
sudo apt update && sudo apt install tmux -y
```

2️⃣ **Configure tmux for a Better Experience**
Create a `~/.tmux.conf` file to customize it:

```sh
nano ~/.tmux.conf
```

Paste the following configuration:

```sh
# Set better keybindings

set -g mouse on # Enable mouse support for easier pane resizing
unbind C-b # Unbind default tmux prefix (Ctrl+b)
set -g prefix C-a # Set "Ctrl + a" as the new prefix (easier to use)
bind C-a send-prefix # Let you send Ctrl+A to applications if needed

# Split panes with shortcuts

bind | split-window -h # Ctrl+A then | → Split horizontally
bind - split-window -v # Ctrl+A then - → Split vertically

# Switch panes with arrow keys

bind -r Left select-pane -L
bind -r Right select-pane -R
bind -r Up select-pane -U
bind -r Down select-pane -D

# Resize panes with Shift + Arrow keys

bind -r S-Left resize-pane -L 5
bind -r S-Right resize-pane -R 5
bind -r S-Up resize-pane -U 5
bind -r S-Down resize-pane -D 5

# Reload config with Ctrl+A then r

bind r source-file ~/.tmux.conf \; display-message "Tmux config reloaded!"
```

Save & exit (**Ctrl+X → Y → Enter**).

3️⃣ **Reload tmux Configuration**

```sh
tmux source ~/.tmux.conf
```

4️⃣ **Start a New tmux Session**

```sh
tmux
```

### Explanation

- **Mouse Support**: `set -g mouse on`

  - Enables mouse support for easier pane resizing and navigation.

- **Prefix Key**: `set -g prefix C-a`

  - Changes the default prefix key from `Ctrl+b` to `Ctrl+a` for easier access.
  - `unbind C-b` unbinds the default prefix key.

- **Send Prefix**: `bind C-a send-prefix`

  - Allows you to send `Ctrl+a` to applications if needed.

- **Split Panes**:

  - `bind | split-window -h`: `Ctrl+a` then `|` splits the window horizontally.
  - `bind - split-window -v`: `Ctrl+a` then `-` splits the window vertically.

- **Switch Panes**:

  - `bind -r Left select-pane -L`: `Ctrl+a` then Left Arrow switches to the left pane.
  - `bind -r Right select-pane -R`: `Ctrl+a` then Right Arrow switches to the right pane.
  - `bind -r Up select-pane -U`: `Ctrl+a` then Up Arrow switches to the upper pane.
  - `bind -r Down select-pane -D`: `Ctrl+a` then Down Arrow switches to the lower pane.

- **Resize Panes**:

  - `bind -r S-Left resize-pane -L 5`: `Shift + Left Arrow` resizes the pane to the left by 5 units.
  - `bind -r S-Right resize-pane -R 5`: `Shift + Right Arrow` resizes the pane to the right by 5 units.
  - `bind -r S-Up resize-pane -U 5`: `Shift + Up Arrow` resizes the pane upwards by 5 units.
  - `bind -r S-Down resize-pane -D 5`: `Shift + Down Arrow` resizes the pane downwards by 5 units.

- **Reload Configuration**:
  - `bind r source-file ~/.tmux.conf \; display-message "Tmux config reloaded!"`: `Ctrl+a` then `r` reloads the tmux configuration file and displays a message.

Now, try these:

- **Split panes:**
  - `Ctrl + A` then `|` (vertical split)
  - `Ctrl + A` then `-` (horizontal split)
- **Switch between panes:** `Ctrl + A` then arrow keys
- **Resize panes:** Shift + Arrow keys
- **Detach from tmux (without closing it):** `Ctrl + A` then `D`
- **Reattach to your session after closing the terminal:**
  ```sh
  tmux attach-session -t 0
  ```
