# Mac-Library-Services 🚀

A collection of native macOS Automations.

Born out of a clutch study session for a BRAC University quiz—where converting PPTX slides to PDF fast was a necessity—this project evolved into a lightweight automation toolkit for power users.

---

## ⚡ Included Modules

### 1. `Open in WezTerm`
- **Goal:** Instantly open a WezTerm terminal instance in the currently selected directory or file location.
- **Smart Line Buffer Injection:** Automatically takes all selected files/folders, formats them with shell escaping (`printf %q`), and populates them into the Zsh `BUFFER`.
- **Cursor Positioning:** Sets the prompt cursor to position `0` (before the filenames), allowing you to type your command immediately without manual navigation.
- **Powerlevel10k & Custom Shell Support:** Uses dynamic `ZDOTDIR` environment redirection to load your native `.zshrc`, `.zprofile`, `fzf`, and `zoxide` setups cleanly without triggering line-wipe issues or `gitstatus` initialization errors.

### 2. `Convert PPTX to PDF`
- **Goal:** Batch convert PowerPoint (`.pptx`) presentations to PDF files directly within Finder.
- **Headless Engine:** Utilizes LibreOffice (`soffice --headless`) under the hood to process documents cleanly without launching full GUI applications.
- **Automated Directory Output:** Outputs converted files right beside their original `.pptx` counterparts in Finder.

---

## 📦 Installation
You can install the Quick Actions manually by copying the workflow bundles directly into your user Services directory.

Run the following command in your terminal:

```bash
# 1. Create the Services directory if it doesn't exist
mkdir -p ~/Library/Services

# 2. Copy the workflows into your Services directory
cp -R Services/*.workflow ~/Library/Services/

# 3. Flush and update the macOS system services cache
pbs -flush && pbs -update

# 4. Reload Finder and LaunchServices to recognize the new actions
/System/Library/Frameworks/CoreServices.framework/Frameworks/LaunchServices.framework/Support/lsregister -kill -r -domain local -domain system -domain user
killall Finder
killall Dock
```
---

## ⌨️ Assigning Global Keyboard Shortcuts

To trigger these actions with a single keystroke:

1. Open **System Settings** > **Keyboard** > **Keyboard Shortcuts...**
2. Select **Services** from the left sidebar.
3. Locate the installed Quick Actions under **Files and Folders** or **General**:
   - For **Open in WezTerm**: Assign a shortcut like `Cmd + Shift + W`.
   - For **Convert PPTX to PDF**: Assign a shortcut like `Cmd + Shift + P`.
4. Click **Done**.


---

## 🛠️ Prerequisites

- **macOS**
- **WezTerm** (`/Applications/WezTerm.app`)
- **LibreOffice** (Installed via Homebrew or standard application path for headless PPTX conversion)
  ```bash
  brew install --cask libreoffice
  ```

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
