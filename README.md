# cmake-storyboard-bug

Has been fixed by https://gitlab.kitware.com/cmake/cmake/-/merge_requests/7562 and will be a part of v3.25.0.

-----

Demonstration of bug with precompiled headers and storyboard in Xcode generator with CMake >= 3.22.0.

```bash
cmake -S . -B build -G Xcode
cmake --build build
```

Build error:

> CompileStoryboard /Users/kambala/dev/macos/cmake-storyboard-bug/Main.storyboard (in target 'cmake-storyboard-bug' from project 'cmake-storyboard-bug')
>
> cd /Users/kambala/dev/macos/cmake-storyboard-bug
>
> /Applications/Xcode13.4.1.app/Contents/Developer/usr/bin/ibtool --errors --warnings --notices --module cmake_storyboard_bug **-DCMAKE_SKIP_PRECOMPILE_HEADERS** --output-partial-info-plist /Users/kambala/dev/macos/cmake-storyboard-bug/build/cmake-storyboard-bug.build/Debug/cmake-storyboard-bug.build/Main-SBPartialInfo.plist --auto-activate-custom-fonts --target-device mac --minimum-deployment-target 12.3 --output-format human-readable-text --compilation-directory /Users/kambala/dev/macos/cmake-storyboard-bug/build/cmake-storyboard-bug.build/Debug/cmake-storyboard-bug.build /Users/kambala/dev/macos/cmake-storyboard-bug/Main.storyboard

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>com.apple.ibtool.errors</key>
	<array>
		<dict>
			<key>description</key>
			<string>Unable to rename classes, class name parsing failed.</string>
		</dict>
		<dict>
			<key>description</key>
			<string>Not enough arguments provided; where is the input document to operate on?</string>
		</dict>
	</array>
</dict>
</plist>
```

> Command CompileStoryboard failed with a nonzero exit code
