# stardoc-prebuilt
Pre-built JAR distribution for https://github.com/bazelbuild/stardoc

Avoids the need to compile Java sources including protobuf.
Workaround for https://github.com/bazelbuild/stardoc/pull/221 which was reverted in
https://github.com/bazelbuild/stardoc/pull/243.

Also avoids the need for rulesets to take lots of transitive dependencies, evidenced by
"Legacy WORKSPACE setup" on https://github.com/bazelbuild/stardoc/releases

Also avoids developers getting logspam from tools they don't have control over, e.g.

```
INFO: From Linking external/protobuf+/src/google/protobuf/io/libio_win32.a [for tool]:
warning: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/libtool: archive library: bazel-out/darwin_arm64-opt-exec-ST-d57f47055a04/bin/external/protobuf+/src/google/protobuf/io/libio_win32.a the table of contents is empty (no object file members in the library define global symbols)
INFO: From Linking external/protobuf+/protoc [for tool]:
ld: warning: ignoring duplicate libraries: '-lm', '-lpthread'
INFO: From Building external/protobuf+/java/core/libcore.jar (43 source files, 1 source jar):
external/protobuf+/java/core/src/main/java/com/google/protobuf/RepeatedFieldBuilderV3.java:28: warning: [dep-ann] deprecated item is not annotated with @Deprecated
public class RepeatedFieldBuilderV3<
       ^
Blah blah some javac warning...
```

## Installing

Read release notes on the release you grab, which should be at the matching version to your `stardoc` bazel_dep.

Also see example at https://github.com/aspect-build/rules_ts/pull/796/files
