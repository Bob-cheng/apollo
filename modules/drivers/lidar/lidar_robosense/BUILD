load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_binary(
    name = "libsuteng_driver_component.so",
    linkshared = True,
    linkstatic = False,
    deps = [":driver"],
)

cc_library(
    name = "driver",
    srcs = glob(
        ["**/*.cpp"]
    ),
    hdrs = glob(
        ["**/*.h"]
    ),
    copts = ['-DMODULE_NAME=\\"suteng\\"'],
    deps = [
        "//cyber",
        "//modules/common/util",
        "//modules/drivers/lidar/lidar_robosense/proto:suteng_proto",
        "//modules/drivers/proto:sensor_proto",
        "@pcl",
        "@eigen",
        "@yaml_cpp//:yaml",
    ],
)

cpplint()
