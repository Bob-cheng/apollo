load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "vehicle_manager",
    srcs = ["vehicle_manager.cc"],
    hdrs = ["vehicle_manager.h"],
    copts = ['-DMODULE_NAME=\\"dreamview\\"'],
    deps = [
        "//cyber",
        "//modules/common/configs:vehicle_config_helper",
        "//modules/common/util",
        "//modules/common/util:string_util",
        "//modules/dreamview/proto:hmi_config_proto",
        "@com_google_absl//absl/strings",
    ],
)

cc_binary(
    name = "vehicle_manager_main",
    srcs = ["vehicle_manager_main.cc"],
    copts = ['-DMODULE_NAME=\\"dreamview\\"'],
    deps = [
        ":vehicle_manager",
    ],
)

cc_test(
    name = "vehicle_manager_test",
    size = "small",
    srcs = ["vehicle_manager_test.cc"],
    data = glob(["testdata/**"]),
    deps = [
        ":vehicle_manager",
        "//modules/common/util",
        "@gtest//:main",
    ],
)

cc_library(
    name = "hmi",
    srcs = ["hmi.cc"],
    hdrs = ["hmi.h"],
    copts = ['-DMODULE_NAME=\\"dreamview\\"'],
    deps = [
        ":hmi_worker",
        "//cyber/common:file",
        "//modules/common/adapters:adapter_gflags",
        "//modules/common/configs:vehicle_config_helper",
        "//modules/common/monitor_log",
        "//modules/common/util:json_util",
        "//modules/common/util:map_util",
        "//modules/dreamview/backend/fuel_monitor:fuel_monitor_manager",
        "//modules/dreamview/backend/handlers:websocket_handler",
        "//modules/dreamview/backend/map:map_service",
        "//modules/dreamview/backend/point_cloud:point_cloud_updater",
    ],
)

cc_library(
    name = "hmi_worker",
    srcs = ["hmi_worker.cc"],
    hdrs = ["hmi_worker.h"],
    copts = ['-DMODULE_NAME=\\"dreamview\\"'],
    deps = [
        ":vehicle_manager",
        "//cyber",
        "//modules/canbus/proto:canbus_proto",
        "//modules/common/adapters:adapter_gflags",
        "//modules/common/configs:config_gflags",
        "//modules/common/kv_db",
        "//modules/common/proto:drive_event_proto",
        "//modules/common/util:future",
        "//modules/common/util:map_util",
        "//modules/common/util:message_util",
        "//modules/control/proto:control_proto",
        "//modules/dreamview/backend/common:dreamview_gflags",
        "//modules/dreamview/backend/fuel_monitor:data_collection_monitor",
        "//modules/dreamview/backend/fuel_monitor:fuel_monitor_manager",
        "//modules/dreamview/backend/fuel_monitor:fuel_monitor_gflags",
        "//modules/dreamview/backend/fuel_monitor:preprocess_monitor",
        "//modules/dreamview/proto:hmi_config_proto",
        "//modules/dreamview/proto:hmi_mode_proto",
        "//modules/dreamview/proto:hmi_status_proto",
        "//modules/localization/proto:localization_proto",
        "//modules/monitor/proto:system_status_proto",
        "@boost",
        "@com_google_absl//absl/strings",
        "@com_google_protobuf//:protobuf",
    ],
)

cc_test(
    name = "hmi_worker_test",
    size = "small",
    srcs = ["hmi_worker_test.cc"],
    deps = [
        ":hmi_worker",
        "@gtest//:main",
    ],
)

cpplint()
