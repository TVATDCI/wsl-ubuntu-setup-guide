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

## **6. Set VS Code to Use Ubuntu (WSL) Terminal**

### **Install WSL Extension in VS Code**

1. Open **VS Code**.
2. Press **Ctrl + Shift + X** to open Extensions.
3. Search for **"Remote - WSL"** and install it.
4. Restart VS Code.

### **Open VS Code with WSL**

```bash
code .
```

### **Set Default Terminal to Ubuntu (Zsh)**

1. Open VS Code settings (**Ctrl + ,**)
2. Search for `terminal.integrated.defaultProfile.windows`.
3. Set it to **Ubuntu (WSL)**.
4. Restart VS Code.

---

## **7. Install Node.js, npm, and Git in Ubuntu**

### **Install Node.js and npm**

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```

Verify installation:

```bash
node -v
npm -v
```

### **Set Up Git and Connect with GitHub**

1. Configure Git username and email:
   ```bash
   git config --global user.name "YourName"
   git config --global user.email "youremail@example.com"
   ```
2. Check if Git is installed:
   ```bash
   git --version
   ```
3. Clone a GitHub repository:
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
\\wsl.localhost\Ubuntu\home\<your-ubuntu-yourname>
```

Or navigate to:

```plaintext
C:\Users\YourWindowsUsername\AppData\Local\Packages\CanonicalGroupLimited...\LocalState\rootfs\home\<your-ubuntu-username>
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
   code .
   ```

   ```

   ```

✅ **Now you have the perfect dual-terminal setup: Windows for daily tasks & Ubuntu for development!** 🚀
