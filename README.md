# batconmod

A small bash script that toggles the battery charge limit (conservation mode) on one specific laptop.

> **Warning: made for one computer only.**
> This script is designed and tested only for my own laptop, a **Lenovo Legion 5 15ARH05 (82B5)** running **CachyOS** (kernel 7.3.0-4-cachyos).
> It has not been tested on any other model. Use it on other hardware at your own risk.

## What it does

Switches the battery between two modes:

- `Long_Life`: limit on, charging stops at about 60%
- `Standard`: limit off, charges to 100%

It does this by writing to `/sys/class/power_supply/BAT0/charge_types`.

## Install

```bash
mkdir -p ~/.local/bin
cp batconmod ~/.local/bin/ && chmod +x ~/.local/bin/batconmod
```

## Usage

```bash
batconmod            # toggle
batconmod on         # limit on (Long_Life)
batconmod off        # limit off (Standard)
batconmod status     # show current state
```

Changing the mode asks for your sudo password. If the battery has no `charge_types` file offering both modes, the script exits with an error and changes nothing.
