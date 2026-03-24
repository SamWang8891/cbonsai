# cbonsai

在終端機中隨機生成美麗的盆栽樹。

![cbonsai 展示](https://i.imgur.com/rnqJx3P.gif)

## 前置需求

你需要 C 編譯器、`make`，以及 ncurses 開發函式庫。

**Ubuntu / Debian：**

```bash
sudo apt update
sudo apt install build-essential libncurses-dev pkg-config
```

**Fedora / RHEL：**

```bash
sudo dnf install gcc make ncurses-devel pkg-config
```

**Arch Linux：**

```bash
sudo pacman -S base-devel ncurses pkg-config
```

**macOS（Homebrew）：**

```bash
brew install ncurses pkg-config
```

## 編譯

1. 複製（clone）這個 repository：

```bash
git clone https://github.com/SamWang8891/cbonsai.git
cd cbonsai
```

2. 編譯：

```bash
make
```

這會在目前的目錄下產生 `cbonsai` 執行檔。

3. （選擇性）清除編譯產物：

```bash
make clean
```

## 安裝

### 方法 A：安裝到系統路徑

```bash
sudo make install
```

這會把 `cbonsai` 安裝到 `/usr/local/bin/`，之後在任何地方都可以直接執行。

移除安裝：

```bash
sudo make uninstall
```

### 方法 B：手動加入 PATH

如果不想使用 `sudo`，可以把編譯目錄加到你的 `PATH` 環境變數。

在 `~/.bashrc`（如果用 Zsh 則是 `~/.zshrc`）的最後加上這行：

```bash
export PATH="$HOME/cbonsai:$PATH"
```

把 `$HOME/cbonsai` 替換成你實際 clone 到的路徑。

然後重新載入設定：

```bash
source ~/.bashrc
```

現在就可以在任何目錄執行 `cbonsai` 了。

## 使用方式

```
cbonsai [選項]
```

**選項：**

| 旗標 | 說明 | 預設值 |
|------|------|--------|
| `-l, --live` | 即時模式：一步步看樹長大 | 關閉 |
| `-t, --time=秒數` | 即時模式下每步的間隔秒數 | `0.03` |
| `-i, --infinite` | 無限模式：持續生成新的樹 | 關閉 |
| `-w, --wait=秒數` | 無限模式下每棵樹之間的間隔秒數 | `4` |
| `-S, --screensaver` | 螢幕保護模式（即時＋無限，按任意鍵退出） | 關閉 |
| `-m, --message=文字` | 在樹旁邊顯示一段文字 | 無 |
| `-b, --base=數字` | 花盆樣式（`0`＝無、`1`＝大、`2`＝小） | `1` |
| `-c, --leaf=清單` | 以逗號分隔的葉子字元清單 | `&` |
| `-M, --multiplier=數字` | 分支倍數，越大分支越多（0–20） | `5` |
| `-L, --life=數字` | 生命值，越大長越多（0–200） | `32` |
| `-p, --print` | 完成後將樹印到終端機 | 關閉 |
| `-s, --seed=數字` | 亂數種子 | 隨機 |
| `-v, --verbose` | 顯示更多除錯資訊 | 關閉 |
| `-h, --help` | 顯示說明 | — |

**範例：**

```bash
# 即時觀看樹的生長過程
cbonsai -l

# 螢幕保護模式
cbonsai -S

# 靜態樹 + 顯示訊息
cbonsai -p -m "Hello!"

# 自訂葉子字元，增加分支數
cbonsai -l -c "*,.,~" -M 10
```

按 `q` 退出（螢幕保護模式下按任意鍵退出）。

## 運作原理

cbonsai 使用 ncurses 在終端機中繪製程序化生成的盆栽樹。樹從主幹開始隨機分支，最終長出葉子。每次執行都會根據亂數種子產生獨一無二的樹。

## 授權條款

[GPL-3.0](LICENSE)

## 致謝

原作者：[jallbrit](https://gitlab.com/jallbrit/cbonsai/)。本 fork 基於 [hortinstein 的版本](https://github.com/hortinstein/cbonsai)。
