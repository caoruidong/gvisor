load("//tools/go_stateify:defs.bzl", "go_library", "go_test")

package(licenses = ["notice"])

load("//tools/go_generics:defs.bzl", "go_template_instance")

go_template_instance(
    name = "seqatomic_parameters",
    out = "seqatomic_parameters.go",
    package = "time",
    suffix = "Parameters",
    template = "//third_party/gvsync:generic_seqatomic",
    types = {
        "Value": "Parameters",
    },
)

go_library(
    name = "time",
    srcs = [
        "arith_arm64.go",
        "calibrated_clock.go",
        "clock_id.go",
        "clocks.go",
        "muldiv_amd64.s",
        "muldiv_arm64.s",
        "parameters.go",
        "sampler.go",
        "sampler_unsafe.go",
        "seqatomic_parameters.go",
        "tsc_amd64.s",
        "tsc_arm64.s",
    ],
    importpath = "gvisor.googlesource.com/gvisor/pkg/sentry/time",
    visibility = ["//pkg/sentry:internal"],
    deps = [
        "//pkg/log",
        "//pkg/metric",
        "//pkg/syserror",
        "//third_party/gvsync",
    ],
)

go_test(
    name = "time_test",
    srcs = [
        "calibrated_clock_test.go",
        "parameters_test.go",
        "sampler_test.go",
    ],
    embed = [":time"],
)
