# cbonsai

A beautifully random bonsai tree generator for your terminal.

![cbonsai demo](https://i.imgur.com/rnqJx3P.gif)

## Prerequisites

You need a C compiler, `make`, and the ncurses development library.

**Ubuntu / Debian:**

```bash
sudo apt update
sudo apt install build-essential libncurses-dev pkg-config
```

**Fedora / RHEL:**

```bash
sudo dnf install gcc make ncurses-devel pkg-config
```

**Arch Linux:**

```bash
sudo pacman -S base-devel ncurses pkg-config
```

**macOS (Homebrew):**

```bash
brew install ncurses pkg-config
```

## Build

1. Clone the repository:

```bash
git clone https://github.com/SamWang8891/cbonsai.git
cd cbonsai
```

2. Compile:

```bash
make
```

This produces a `cbonsai` binary in the current directory.

3. (Optional) Clean build artifacts:

```bash
make clean
```

## Install

### Option A: System-wide install

```bash
sudo make install
```

This installs `cbonsai` to `/usr/local/bin/`. You can now run `cbonsai` from anywhere.

To uninstall:

```bash
sudo make uninstall
```

### Option B: Add to your PATH manually

If you prefer not to use `sudo`, you can add the build directory to your `PATH`.

Add this line to the end of your `~/.bashrc` (or `~/.zshrc` if you use Zsh):

```bash
export PATH="$HOME/cbonsai:$PATH"
```

Replace `$HOME/cbonsai` with the actual path to the cloned directory.

Then reload your shell:

```bash
source ~/.bashrc
```

Now you can run `cbonsai` from any directory.

## Usage

```
cbonsai [OPTIONS]
```

**Options:**

| Flag | Description | Default |
|------|-------------|---------|
| `-l, --live` | Live mode: watch the tree grow step by step | off |
| `-t, --time=TIME` | Seconds between growth steps (live mode) | `0.03` |
| `-i, --infinite` | Infinite mode: keep generating new trees | off |
| `-w, --wait=TIME` | Seconds between trees (infinite mode) | `4` |
| `-S, --screensaver` | Screensaver mode (live + infinite, quit on keypress) | off |
| `-m, --message=STR` | Display a message next to the tree | none |
| `-b, --base=INT` | Plant base style (`0` = none, `1` = large, `2` = small) | `1` |
| `-c, --leaf=LIST` | Comma-separated list of leaf characters | `&` |
| `-M, --multiplier=INT` | Branch multiplier; higher = more branches (0–20) | `5` |
| `-L, --life=INT` | Life; higher = more growth (0–200) | `32` |
| `-p, --print` | Print tree to terminal when finished | off |
| `-s, --seed=INT` | Seed for the random number generator | random |
| `-v, --verbose` | Increase output verbosity | off |
| `-h, --help` | Show help | — |

**Examples:**

```bash
# Watch a tree grow in real time
cbonsai -l

# Screensaver mode
cbonsai -S

# Static tree with a message
cbonsai -p -m "Hello!"

# Custom leaves and extra branching
cbonsai -l -c "*,.,~" -M 10
```

Press `q` to quit (or any key in screensaver mode).

## How It Works

cbonsai uses ncurses to draw a procedurally generated bonsai tree in your terminal. The tree grows from a trunk that randomly branches into shoots, which eventually sprout leaves. Each run produces a unique tree based on the random seed.

## License

[GPL-3.0](LICENSE)

## Credits

Originally created by [jallbrit](https://gitlab.com/jallbrit/cbonsai/). This fork is based on [hortinstein's version](https://github.com/hortinstein/cbonsai).
