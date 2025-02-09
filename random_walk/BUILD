# Random Walk Test for RDMA.

package(
    default_testonly = True,
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],
)

cc_test(
    name = "random_walk_test",
    srcs = ["random_walk_test.cc"],
    linkstatic = 1,
    shard_count = 2,
    deps = [
        "//cases:gunit_main",
        "//public:introspection",
        "//random_walk/internal:multi_node_orchestrator",
        "//random_walk/internal:random_walk_config_cc_proto",
        "//random_walk/internal:single_node_orchestrator",
        "@com_glog_glog//:glog",
        "@com_google_absl//absl/time",
        "@libibverbs",
    ],
)

# random_walk_test_library is a library to support reuse of random walk test.
cc_library(
    name = "random_walk_test_library",
    testonly = 1,
    srcs = ["random_walk_test.cc"],
    deps = [
        "//public:introspection",
        "//random_walk/internal:multi_node_orchestrator",
        "//random_walk/internal:random_walk_config_cc_proto",
        "//random_walk/internal:single_node_orchestrator",
        "@com_glog_glog//:glog",
        "@com_google_absl//absl/time",
        "@com_google_googletest//:gtest",
    ],
    alwayslink = 1,
)

cc_binary(
    name = "run_random_walk",
    srcs = ["random_walk_main.cc"],
    deps = [
        ":flags",
        "//internal:introspection_mlx4",
        "//internal:introspection_mlx5",
        "//internal:introspection_rxe",
        "//public:introspection",
        "//random_walk/internal:multi_node_orchestrator",
        "//random_walk/internal:random_walk_config_cc_proto",
        "//random_walk/internal:single_node_orchestrator",
        "@com_glog_glog//:glog",
        "@com_google_absl//absl/debugging:failure_signal_handler",
        "@com_google_absl//absl/flags:flag",
        "@com_google_absl//absl/flags:parse",
        "@com_google_absl//absl/time",
        "@com_google_googletest//:gtest",
    ],
)

cc_library(
    name = "flags",
    srcs = ["flags.cc"],
    hdrs = ["flags.h"],
    deps = ["@com_google_absl//absl/flags:flag"],
)
