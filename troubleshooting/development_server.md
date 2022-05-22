# COULD NOT CONNECT TO DEVELOPMENT SERVER

Usually Android device doesn't know how to talk to dev server (port not open).

```sh
adb reverse tcp:8081 tcp:8081
```

Make sure packager running before manually running app.

If port taken, check if multiple RN apps running.

In iOS `Info.plist`, set `NSAllowsArbitraryLoads` and `NSAllowsLocalNetworking` to `true` (already by default).

- In iOS 9 and macOS 10.11, App Transport Security (ATS) disallows connections to unqualified domains, .local domains, and IP addresses. Can add exceptions for unqualified and .local domains in `NSExceptionDomains` dictionary, but not numerical IP addresses. Instead use `NSAllowsArbitraryLoads` to load directly from IP address.
- In iOS 10 and macOS 10.12 and later, ATS allows all 3 connections by default. For backward compatibility, set both `NSAllowsArbitraryLoads` and `NSAllowsLocalNetworking` to `true`.
