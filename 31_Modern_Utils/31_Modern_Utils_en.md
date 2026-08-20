# Modern Utilities

## bat (improved cat)

```bash
# Installation
sudo pacman -S bat

# Usage
bat file.txt

# With line numbers
bat -n file.txt

# With language highlighting
bat -l python file.py

# In pager
bat -p file.txt
```

## exa/eza (improved ls)

```bash
# Installation
sudo pacman -S eza

# Usage
eza

# With details
eza -la

# With tree
eza --tree

# With icons
eza --icons

# With colors
eza -la --color=always
```

## fd (improved find)

```bash
# Installation
sudo pacman -S fd

# Usage
fd pattern

# Search by name
fd "*.txt"

# Search in directory
fd pattern /path

# By file type
fd -t f pattern
fd -t d pattern

# Ignore .gitignore
fd --no-ignore pattern
```

## ripgrep (improved grep)

```bash
# Installation
sudo pacman -S ripgrep

# Usage
rg pattern

# Search in file
rg pattern file.txt

# Recursive
rg pattern /path

# With context
rg -C 3 pattern

# With line numbers
rg -n pattern

# By file type
rg -t py pattern
```

## fzf (fuzzy finder)

```bash
# Installation
sudo pacman -S fzf

# Usage
# Find files
find . | fzf

# Search history
history | fzf

# With preview
fzf --preview 'cat {}'

# Vim integration
vim $(fzf)

# Cd integration
cd $(find -type d | fzf)
```

## zoxide (improved cd)

```bash
# Installation
sudo pacman -S zoxide

# Add to .bashrc
eval "$(zoxide init bash)"

# Usage
z pattern

# Interactive
zi
```

## starship (prompt)

```bash
# Installation
sudo pacman -S starship

# Add to .bashrc
eval "$(starship init bash)"
```

## dust (improved du)

```bash
# Installation
sudo pacman -S dust

# Usage
dust

# In directory
dust /path

# With limit
dust -n 10
```

## duf (improved df)

```bash
# Installation
sudo pacman -S duf

# Usage
duf

# Specific disks
duf /dev/sda1
```

## procs (improved ps)

```bash
# Installation
sudo pacman -S procs

# Usage
procs

# By name
procs nginx

# Tree
procs --tree
```

## Quick Reference

```bash
# Install all
sudo pacman -S bat eza fd ripgrep fzf zoxide starship dust duf procs

# Quick search
rg "pattern" .

# Find file
fd "name"

# Fuzzy find
find . | fzf

# Beautiful ls
eza -la --icons

# Beautiful cat
bat file.txt
```
