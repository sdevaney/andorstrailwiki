---
description: >-
  This guide walks through setting up your development environment to contribute
  code to Andor's Trail.
---

# Development Environment Setup

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

* Java Development Kit (JDK) 8 or higher
* Git
* Android SDK (API level 21 or higher)
* 4+ GB RAM recommended
* 2+ GB disk space for Android SDK

### Step 1: Install Java Development Kit (JDK) <a href="#step-1-install-java-development-kit-jdk" id="step-1-install-java-development-kit-jdk"></a>

### Windows

1. Download JDK from [oracle.com](https://www.oracle.com/java/technologies/downloads/) or use [OpenJDK](https://openjdk.org/).
2. Run the installer and follow the prompts.
3. Note the installation directory (e.g., `C:\Program Files\Java\jdk-11.0.x`).
4. Set environment variables:
   * Right-click "This PC" → Properties → Advanced system settings.
   * Click "Environment Variables".
   * Add new system variable:
     * Name: `JAVA_HOME`
     * Value: `C:\Program Files\Java\jdk-11.0.x` (your JDK path)
   * Add to PATH: `%JAVA_HOME%\bin`
5. Verify: Open Command Prompt and run `java -version`

### macOS

```bash
bash# Using Homebrew
brew install openjdk@11

# Set JAVA_HOME in ~/.zshrc or ~/.bash_profile
export JAVA_HOME=/usr/local/opt/openjdk@11

# Verify
java -version
```

### Linux (Ubuntu/Debian)

```bash
bashsudo apt update
sudo apt install openjdk-11-jdk

# Verify
java -version
```

### Step 2: Install Android Studio <a href="#step-2-install-android-studio" id="step-2-install-android-studio"></a>

### Windows & macOS

1. Download from [developer.android.com](https://developer.android.com/studio)
2. Run the installer and follow the prompts.
3. Choose "Custom Setup" to select components:
   * Android SDK
   * Android SDK Platform-Tools
   * Android Emulator
   * Android SDK Build-Tools
4. Accept license agreements.
5. Specify Android SDK location (default: \~/Android/sdk).

### Linux

```bash
bash# Download Android Studio
# Extract to ~/android-studio
tar -xzf android-studio-linux.tar.gz -C ~/

# Add to PATH in ~/.bashrc
export PATH="$PATH:~/android-studio/bin"

# Run
./android-studio/bin/studio.sh
```

### Step 3: Install Git <a href="#step-3-install-git" id="step-3-install-git"></a>

### Windows

* Download from [git-scm.com](https://git-scm.com/).
* Use default installation settings.
* Verify: Open Command Prompt, run `git --version`

### macOS

```bash
bashbrew install git
git --version
```

### Linux

```bash
bashsudo apt install git
git --version
```

### Step 4: Clone Andor's Trail Repository <a href="#step-4-clone-andors-trail-repository" id="step-4-clone-andors-trail-repository"></a>

```bash
bash# Navigate to desired directory
cd ~/Development

# Clone repository
git clone https://github.com/AndorsTrailRelease/andors-trail.git
cd andors-trail

# Verify structure
ls -la
```

You should see:

```
textAndorsTrail/          # Main game module
AndorsTrailEdit/      # Legacy editor
travis/               # CI/CD scripts
.git/                 # Git directory
README.md
```

### Step 5: Open Project in Android Studio <a href="#step-5-open-project-in-android-studio" id="step-5-open-project-in-android-studio"></a>

1. Launch Android Studio.
2. Click "Open" or "File → Open..."
3. Navigate to the cloned repository root.
4. Select the folder and click "OK".
5. Android Studio will index the project (this may take 1-2 minutes).
6. Let Gradle sync complete (bottom status bar shows "Gradle sync successful").

### Step 6: Configure SDK in Android Studio <a href="#step-6-configure-sdk-in-android-studio" id="step-6-configure-sdk-in-android-studio"></a>

If Android SDK is not detected:

1. Go to File → Settings (or Android Studio → Preferences on macOS).
2. Navigate to Appearance & Behavior → System Settings → Android SDK.
3. Click "Edit" next to "Android SDK Location".
4. Select your SDK directory (typically \~/Android/sdk).
5. Click "Next" and "Finish".
6. Let the download complete.

### Step 7: Build the Project <a href="#step-7-build-the-project" id="step-7-build-the-project"></a>

### Using Android Studio GUI

1. Click Build → Make Project.
2. Wait for the build to complete.
3. Check the "Build" tab for the success message.

### Using Command Line

```bash
bash# Navigate to project root
cd andors-trail

# Build APK
./gradlew assembleDebug

# Build signed APK
./gradlew assembleRelease
```

### Step 8: Run on Emulator or Device <a href="#step-8-run-on-emulator-or-device" id="step-8-run-on-emulator-or-device"></a>

### Create Virtual Device (Emulator)

1. Tools → Device Manager.
2. Click "Create Device".
3. Select a device definition (e.g., Pixel 4).
4. Select API Level (21+).
5. Click "Finish".
6. Devices will appear in Device Manager.

### Run on Emulator

1. Click Run → Run 'AndorsTrail'.
2. Select the emulator device.
3. Click "OK".
4. App will launch in the emulator.

### Run on Physical Device

1. Enable Developer Mode on Android device:
   * Go to Settings → About Phone.
   * Tap "Build Number" 7 times.
   * Developer options now appear in Settings.
2. Enable USB Debugging in Developer Options.
3. Connect the device via USB.
4. Click Run → Run 'AndorsTrail'.
5. Select a physical device.
6. Click "OK".

### Step 9: View Javadoc and API Sources <a href="#step-9-view-javadoc-and-api-sources" id="step-9-view-javadoc-and-api-sources"></a>

### View Android API Documentation

1. In Android Studio, click Help → Download PDF Documentation.
2. Or visit [developer.android.com/reference](https://developer.android.com/).

### Generate Project Javadoc

```bash
bash./gradlew javadoc
```

Output appears in `build/docs/javadoc/`

### View Source Code

Right-click any class and select "Go to Definition" or press Ctrl+Click (Cmd+Click on macOS).

### Step 10: Set Up Debugging <a href="#step-10-set-up-debugging" id="step-10-set-up-debugging"></a>

### Enable Debugging in Android Studio

1. Preferences → Debugger → General.
2. Set breakpoints by clicking in the code margin.
3. Run → Debug 'AndorsTrail'.
4. The debugger will stop at breakpoints.
5. Use the Variables panel to inspect the object state.

### View Logcat

1. View → Tool Windows → Logcat.
2. Filter logs by app name: `com.gpl.rpg.AndorsTrail`
3. Set log level (Verbose, Debug, Info, Warning, Error).

### Offline Setup (No Internet Access) <a href="#offline-setup-no-internet-access" id="offline-setup-no-internet-access"></a>

If developing offline, you can still build the project:

### Appendix A: Pre-Downloaded SDK Setup

1. On a connected computer, download Android SDK build-tools and platforms.
2. Copy `~/Android/sdk/` directory to USB drive.
3. Transfer to offline machine: `~/Android/sdk/`
4. Android Studio will detect the pre-existing SDK.

### Appendix B: Gradle Wrapper

The project includes `gradlew` wrapper, which downloads Gradle automatically. First build requires the internet.

### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

### "SDK Location Not Found"

Create file `local.properties` in project root:

```
textsdk.dir=/path/to/android/sdk
```

### "Gradle Sync Failed"

1. File → Invalidate Caches and Restart.
2. Or: `./gradlew clean build --refresh-dependencies`

### "Java Home Not Set"

Set environment variable:

* Windows: See Step 1.
* macOS/Linux: `export JAVA_HOME=$(which java)`

### "Emulator Not Starting"

1. File → Settings → System Settings → Emulation Settings.
2. Enable "Use Host GPU".
3. Allocate more RAM (Device Manager → Edit Device).

### "App Crashes on Launch"

1. Check Logcat for error messages.
2. Verify Android API level (21+).
3. Check AndroidManifest.xml permissions.

### Next Steps <a href="#next-steps" id="next-steps"></a>

1. Read the [**Code Contribution Workflow**](./) guide.
2. Explore [**Core Code Components**](core-code-components.md) documentation.
3. Review existing issues on the forums.
4. Choose an issue to work on.
5. Create a feature branch: `git checkout -b feature/issue-name`

### Development Workflow <a href="#development-workflow" id="development-workflow"></a>

1. Make code changes.
2. Run tests: `./gradlew test`
3. Build APK: `./gradlew assembleDebug`
4. Test on device/emulator.
5. Commit changes: `git commit -m "Description"`
6. Push to fork: `git push origin feature/issue-name`
7. Create Pull Request on GitHub.

### Useful Commands <a href="#useful-commands" id="useful-commands"></a>

```bash
bash# Clean build
./gradlew clean

# Build without testing
./gradlew build -x test

# Run specific tests
./gradlew test --tests com.gpl.rpg.AndorsTrail.SomeTest

# Check for lint errors
./gradlew lint

# Generate APK
./gradlew assembleDebug  # Debug APK
./gradlew assembleRelease # Release APK

# View dependencies
./gradlew dependencies
```

### Resources <a href="#resources" id="resources"></a>

* [Android Developer Documentation](https://developer.android.com/docs)
* [Gradle Build System](https://gradle.org/)
* [Java Documentation](https://docs.oracle.com/javase/)
* [Andor's Trail GitHub](https://github.com/AndorsTrailRelease/andors-trail)
* [Andor's Trail Forums](https://andorstrail.com/)
