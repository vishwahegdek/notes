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

To comile and run the code
```bash
javac Main.java
java Main
```

## 🚀 When to Move to IntelliJ from VS Code

You might want to switch if:

- You start working with Maven/Gradle projects

- You want advanced refactoring tools

- You're doing Spring Boot development