# dotfiles

## Installation on a New Machine

To deploy these dotfiles onto a new machine, open a terminal and run the following commands.

### 1. Define the temporary alias
```bash
alias config='/usr/bin/git --git-dir=HOME/.dotfiles/ --work-tree=HOME'
```

### 2. Clone the repository as bare
Clone the repository data directly into the hidden `.dotfiles` directory:
```bash
git clone --bare git@github.com:alextheo02/dotfiles.git \$HOME/.dotfiles
```

### 3. Hide untracked files
Ensure Git does not display your entire home directory as untracked files:
```bash
config config --local status.showUntrackedFiles no
```

### 4. Checkout the actual configuration files
```bash
config checkout
```

*Note: If the checkout fails with an error indicating that existing files would be overwritten, back up those default files (e.g., `mv ~/.bashrc ~/dotfiles-backup/`) and re-run `config checkout`.*

---

## Day-to-Day Usage

Manage your configuration files using the `config` alias exactly like standard Git.

### View modified configurations
```bash
config status
```

### Track a new file or directory
Because an allowlist is configured in `.gitignore`, you may need the force (`-f`) flag to track a new configuration file:
```bash
config add -f ~/.config/new-tool/config
```

### Save and push changes
```bash
config commit -m "Update configurations"
config push
```
