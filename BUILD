package(default_visibility = ["//visibility:public"])

cc_library(
    name = "lwpr",
    srcs = [
        "src/lwpr.c",
        "src/lwpr_script.c",
    ],
    includes = [
        "include",
    ],
    textual_hdrs = [
        "include/lwpr.h",
    ],
    deps = ["//experimental/users/sschaal/SL/utilities:utility"],
)

cc_binary(
    name = "xlwpr",
    srcs = [
        "src/lwpr_main.c",
        "src/lwpr_test.c",
    ],
    includes = [
        "-Iinclude",
        "-Iutilities/include",
    ],
    deps = [
        ":lwpr",
        "//experimental/users/sschaal/SL/utilities:utility",
    ],
)

cc_binary(
    name = "xascii2clmcplot",
    srcs = ["src/ascii2mrdplot.c"],
    includes = [
        "include",
    ],
    deps = [
        ":lwpr",
        "//experimental/users/sschaal/SL/utilities:utility",
    ],
)
