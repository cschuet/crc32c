# Bazel Build for [google/crc32c](https://github.com/google/crc32c)

Add to your WORKSPACE

```
http_archive(
    name = "com_github_cschuet_crc32c",
    sha256 = "81adcc96018fe226ae9b32eba74ffea266409891f220ad85fdd043d80edae598",
    strip_prefix = "crc32c-858907d2ed420b0738941df751c85a7c7588a7b6",
    urls = [
        "https://github.com/cschuet/crc32c/archive/858907d2ed420b0738941df751c85a7c7588a7b6.tar.gz",
    ],
)

load("@com_github_cschuet_crc32c//:bazel/repositories.bzl", "repositories")

repositories()
```

Compile with
```
bazel build @com_github_google_crc32c//:crc32c
```

Test with
```
bazel test @com_github_google_crc32c//...
```

## Limitations
* not using SSE42
* assumes x86
* assumes STRONG GETAUXVAL
* assumes WEAK GETAUXVAL
* assumes little endian
