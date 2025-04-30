
# 📝 vi Editor Cheatsheet (Ubuntu)

## 🔧 Opening a File
```bash
vi filename.txt
```
- Opens existing file or creates a new one.

---

## 🧭 Modes in vi
- **Normal Mode** – Default, for navigation/commands.
- **Insert Mode** – For typing/editing text.
- **Visual Mode** – For selecting/manipulating text.

---

## ✍️ Switch Modes
- `i` → Insert Mode (start typing)
- `Esc` → Normal Mode

---

## 💾 Save & Exit
- `:w` → Save  
- `:q` → Quit  
- `:wq` or `ZZ` → Save & Quit  
- `:q!` → Quit without saving

---

## 🧭 Navigation (Normal Mode)
- `h` `j` `k` `l` → Left, Down, Up, Right
- `G` → Go to last line  
- `gg` → Go to first line  
- `:n` → Go to line number `n`

---

## ✂️ Editing
- `dd` → Delete line  
- `yy` → Copy (yank) line  
- `p` → Paste  
- `u` → Undo  
- `x` → Delete character  
- `r<char>` → Replace single character

---

## 🔍 Search
- `/word` → Search forward  
- `?word` → Search backward  
- `n` / `N` → Next/Previous match

---

## 🆘 Tips
- Press `Esc` twice if stuck  
- Use `:help` in vi for built-in docs

---

Happy editing! 🚀
