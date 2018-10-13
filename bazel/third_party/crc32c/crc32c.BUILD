licenses(["notice"])

exports_files(["LICENSE"])

package(
    default_visibility = ["//visibility:public"],
)

genrule(
    name = "crc32c_config_h",
    srcs = ["@com_github_cschuet_crc32c//bazel/third_party/crc32c:crc32c_config.h"],
    outs = ["include/crc32c/crc32c_config.h"],
    cmd = "cp $< $@",
)

cc_library(
    name = "crc32c",
    srcs = [
        "src/crc32c.cc",
	"src/crc32c_portable.cc",
    ],
    hdrs = [
        "include/crc32c/crc32c.h",
        "include/crc32c/crc32c_config.h",
	"src/crc32c_arm64.h",
	"src/crc32c_arm64_linux_check.h",
	"src/crc32c_internal.h",
	"src/crc32c_prefetch.h",
	"src/crc32c_read_le.h",
	"src/crc32c_sse42.h",
	"src/crc32c_sse42_check.h",
	"src/crc32c_round_up.h",
    ],
    includes = ["include"],
)

cc_library(
    name = "test_helpers",
    hdrs = ["src/crc32c_extend_unittests.h"],
    deps = [
        ":crc32c",
    ],
)

[cc_test(
    name = src.replace("/", "_").replace(".cc", ""),
    srcs = [src],
    deps = [
	":crc32c",
	":test_helpers",
        "@com_google_googletest//:gtest_main",
    ],
) for src in glob(
    ["**/*_unittest.cc"],
)]
