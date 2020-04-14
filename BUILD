# Every SL directory has a symbolic link to config/bazel to access the config files as local path.
# While not pretty, this allows BUILD files to be independt of the SL_ROOT workspace path, and only
# SL.bzl needs to be adjusted
load(":bazel/SL.bzl", "SL_ROOT", "SL_ROOT_WS")

package(default_visibility = [SL_ROOT + ":__subpackages__"])

licenses(["notice"])

exports_files(["LICENSE"])

# Every SL directory has a symbolic link to config/bazel to access the config files as local path.
# While not pretty, this allows BUILD files to be independt of the SL_ROOT workspace path, and only
# SL.bzl needs to be adjusted

load(":bazel/SL.bzl", "SL_ROOT")

# LWPR is a libary for locally wighted projection regression. While hardly used in SL anymore, it
# is usual for various real-time learning problems with locally weighted regression approaches.

# the core LWPR library
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
    deps = [SL_ROOT + "utilities:utility"],
)

# a binary that can perform function fitting on given data files and a specification file
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
        SL_ROOT + "utilities:utility",
    ],
)

# a binary to analze the statistics in a lwrp structure file
cc_binary(
    name = "xlwprstat",
    srcs = [
        "src/lwpr_main.c",
        "src/lwpr_stat.c",
    ],
    includes = [
        "-Iinclude",
        "-Iutilities/include",
    ],
    deps = [
        ":lwpr",
        SL_ROOT + "utilities:utility",
    ],
)

# a conversion executable to convert ascii matrix data into CLMCPLOT, a matlab
# visualization tool
cc_binary(
    name = "xascii2clmcplot",
    srcs = ["src/ascii2mrdplot.c"],
    includes = [
        "include",
    ],
    deps = [
        ":lwpr",
        SL_ROOT + "utilities:utility",
    ],
)
