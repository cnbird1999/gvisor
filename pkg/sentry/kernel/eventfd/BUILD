package(licenses = ["notice"])  # Apache 2.0

load("//tools/go_stateify:defs.bzl", "go_library", "go_stateify", "go_test")

go_stateify(
    name = "eventfd_state",
    srcs = [
        "eventfd.go",
    ],
    out = "eventfd_state.go",
    package = "eventfd",
)

go_library(
    name = "eventfd",
    srcs = [
        "eventfd.go",
        "eventfd_state.go",
    ],
    importpath = "gvisor.googlesource.com/gvisor/pkg/sentry/kernel/eventfd",
    visibility = ["//pkg/sentry:internal"],
    deps = [
        "//pkg/abi/linux",
        "//pkg/refs",
        "//pkg/sentry/context",
        "//pkg/sentry/fs",
        "//pkg/sentry/fs/anon",
        "//pkg/sentry/fs/fsutil",
        "//pkg/sentry/usermem",
        "//pkg/state",
        "//pkg/syserror",
        "//pkg/waiter",
        "//pkg/waiter/fdnotifier",
    ],
)

go_test(
    name = "eventfd_test",
    size = "small",
    srcs = ["eventfd_test.go"],
    embed = [":eventfd"],
    deps = [
        "//pkg/sentry/context/contexttest",
        "//pkg/sentry/usermem",
        "//pkg/waiter",
    ],
)
