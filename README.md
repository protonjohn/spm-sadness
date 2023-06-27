# SPM Sadness

This is a test project that demonstrates the following warning in the
build log of the app, which will cause a rejection from TestFlight:

```
warning: invalid character in Bundle Identifier. This string must be a uniform type identifier (UTI) that contains only alphanumeric (A-Z,a-z,0-9), hyphen (-), and period (.) characters. (in target '_SwiftUINavigationState' from project 'swiftui-navigation')
```

To reproduce, please run `xcodebuild -workspace spm-sadness.xcworkspace -scheme FooApp`
