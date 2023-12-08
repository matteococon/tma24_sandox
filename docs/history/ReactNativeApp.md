# Create a React Native 2023 sub project

Reference: <https://reactnative.dev/docs/environment-setup?guide=native&platform=android>

## Node & Watchman

```sh
# node --version # ndoejs is required
mkdir -p app/src_rn23 ; cd app/src_rn23
brew update
brew install watchman
```

## Java Development Kit

Install the OpenJDK distribution called `Azul Zulu` using `Homebrew`:

```sh
brew tap homebrew/cask-versions
brew install --cask zulu17

# Get path to where cask was installed to double-click installer
brew info --cask zulu17
```

After you install the JDK, update your `JAVA_HOME` environment variable.
If you used above steps, `JDK` will likely be at `/Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home`

The `Zulu OpenJDK` distribution offers JDKs for _both Intel and M1 Macs_. This will make sure your builds are faster on M1 Macs compared to using an Intel-based JDK.

> Note: If you have already installed JDK on your system, we recommend JDK 17. You may encounter problems using higher JDK versions.

```sh
java --version
echo $JAVA_HOME
```

## Android development environment

1. Install Android Studio: <https://developer.android.com/studio/index.html>
2. Install the Android SDK, then make sure the following items are checked:

   - `Android SDK Platform 33`
   - `Google APIs ARM 64 v8a System Image`

3. Configure the ANDROID_HOME environment variable, adding the following lines to your ~/.zprofile or ~/.zshrc:

```sh
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

> Note: Run `source ~/.zprofile` to reload the new config
> Note: Please make sure you use the correct Android SDK path. You can find the actual location of the SDK in the Android Studio "Settings" dialog, under "Languages & Frameworks" → "Android SDK".

```sh
echo $ANDROID_HOME
echo $PATH
```

## Creating a new application

```sh
npx react-native@latest init RN23
```

output:

```output
  Run instructions for Android:
    • Have an Android emulator running (quickest way to get started), or a device connected.
    • cd "./app/src_rn23/RN23" && npx react-native run-android

  Run instructions for iOS:
    • cd "./app/src_rn23/RN23" && npx react-native run-ios
    - or -
    • Open RN23/ios/RN23.xcworkspace in Xcode or run "xed -b ios"
    • Hit the Run button

  Run instructions for macOS:
    • See https://aka.ms/ReactNativeGuideMacOS for the latest up-to-date instructions.
```

launch an Android emulator:

```sh
$ANDROID_HOME/emulator/emulator -avd AppiumUITests-generic_13 &
cd app/src_rn23/RN23
npm start
# then select "run Android", or via cli use:
# npm run android
```

Now you can modify `app/src_rn23/RN23/App.tsx`.
To see changes:

- Save file
- or select Reload from the Dev Menu (Cmd ⌘ + M)
