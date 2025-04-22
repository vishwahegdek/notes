## Switching java versions

✅ Install Java 21 alongside Java 24 (Recommended) On Ubuntu/Linux

```bash
sudo apt install openjdk-21-jdk
```
✅ Switching java versions

```bash
sudo update-alternatives --config java
```

🔍 How to Check Java Version Being Used
```bash
java -version
```

To verify which Java your Maven uses:

```bash
mvn -v
```