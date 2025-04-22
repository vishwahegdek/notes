## Installing .deb packages
✅ Using dpkg
```bash
sudo dpkg -i package_name.deb
```
Replace package_name.deb with the actual file name.

If you see any dependency issues, run:

```bash
sudo apt-get install -f
```
This will fix broken dependencies.

✅ Using apt (preferred, handles dependencies better)
```bash
sudo apt install ./package_name.deb
```