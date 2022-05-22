# Command PhaseScriptExecution failed

Typically M1 issue for iOS.

1. Delete `Podfile.lock`.
2. Delete `Pods` folder.
3. Delete `.xcworkspace`.
4. Pod install.
5. Clean build folder.

In Xcode: target > **Build Phases** > **Bundle React Native code and images**

- check **Run script: For install builds only**
