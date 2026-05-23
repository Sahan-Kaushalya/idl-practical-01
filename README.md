# idl-practical-01

TestApp — Java IDL practical 01 sample application.

මෙය IDL practical 01 සඳහා Java උදාහරණ යෙදුමකි.

## Project structure
- `TestApp/` — Java source files (generated stubs and helpers)
	- `_TestStub.java`
	- `Test.java`
	- `TestHelper.java`
	- `TestHolder.java`
	- `TestOperations.java`
	- `TestPOA.java`
- `TestApp.idl` — IDL file used to generate the stubs

## Requirements
- Java JDK 8 

## Build & Run
Open a terminal in the project root and compile the Java sources, then run the `Test` class.

Windows (PowerShell / CMD):
```bash
javac TestApp\*.java
java Test
```

Unix / macOS:
```bash
javac TestApp/*.java
java Test
```

If your project uses a generated package or different entrypoint, adjust the commands accordingly.

## Notes
- Edit `TestApp.idl` and regenerate stubs if you change the IDL.
- If `Test` requires runtime arguments or a classpath, pass them to the `java` command.

## CORBA Setup (Java)
This project uses CORBA-compatible stubs. CORBA support is available in older Java versions such as Java 8 (JDK 1.8).

1. Verify Java is installed:

```bash
java -version
```

2. (Windows PowerShell) Temporarily prepend JDK 1.8 to your `PATH` for the current session:

```powershell
$env:Path = "C:\Program Files\Java\jdk1.8.0_202\bin;$env:Path"
```

3. Compile the Java sources from the project root. Examples (adjust for your package layout):

Windows:
```powershell
javac TestApp\*.java
# or if sources are at root or under packages:
javac *.java com\*.java
```

Unix / macOS:
```bash
javac TestApp/*.java
# or with packages:
javac *.java com/*.java
```

4. Naming service (`tnameserv`):
- Default port commonly used with the reference implementation is `900`.
- To start the naming service on port `1050`:

```bash
tnameserv -ORBInitialPort 1050
```

Run `tnameserv -help` for platform-specific options if available.

5. Run the application (after starting `tnameserv` in a separate terminal):

```bash
java Test -ORBInitialPort 1050
```

If your server and client are in packages, use the fully-qualified class name and ensure the classpath includes the compiled classes (for example, `java -cp . com.example.Test -ORBInitialPort 1050`).

Notes:
- If you change `TestApp.idl`, regenerate the stubs and recompile.
- On modern Java versions (>= 11), CORBA components were removed; prefer JDK 1.8 for built-in CORBA support or use an external CORBA implementation.

If you want, I can also add example commands to run the server and client separately, or include a small script to start `tnameserv` and then run the app.
