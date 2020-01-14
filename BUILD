package(default_visibility = ["//visibility:public"])
load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")

cc_library(
    name = "lwpr",
    srcs = [
	"src/lwpr.c", 
	"src/lwpr_script.c"
    ],
    hdrs = [
	"include/lwpr.h"
    ],
    includes = [
    	"include"
	],
    deps = ["//utilities:utility"],
    visibility = ["//visibility:public"],
)

cc_binary(
    name = "xlwpr",
    srcs = ["src/lwpr_main.c","src/lwpr_test.c"],
    includes = [
    	"-Iinclude",
    	"-Iutilities/include"
	],
    deps = [
        ":lwpr"
    ],
)

cc_binary(
    name = "xascii2clmcplot",
    srcs = ["src/ascii2mrdplot.c"],
    includes = [
    	"include"
	],
    deps = [
        ":lwpr",
        "//utilities:utility"		
    ],
)
