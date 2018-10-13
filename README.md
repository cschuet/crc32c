# Bazel Build for [google/crc32c](https://github.com/google/crc32c)

Add to your WORKSPACE

```
http_archive(
    name = "com_github_cschuet_crc32c",
    sha256 = "2c672d6346b1cbc2237bc73aeb704c1f9bd1c9fc59fe78a24136f037279b8b31",
    strip_prefix = "crc32c-6630c87e182658c08d5528fc55e9a26c02600909",
    urls = [
        "https://github.com/cschuet/crc32c/archive/6630c87e182658c08d5528fc55e9a26c02600909.tar.gz",
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
