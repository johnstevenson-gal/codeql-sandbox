# Reworked keras optimizer. For more context, please refer to go/new-keras-optimizer.

load("@org_keras//keras:keras.bzl", "distribute_py_test")

package(
    default_visibility = [
        "//keras:friends",
    ],
    licenses = ["notice"],
)

py_library(
    name = "optimizer",
    srcs = [
        "__init__.py",
        "adadelta.py",
        "adagrad.py",
        "adam.py",
        "adamax.py",
        "adamw.py",
        "ftrl.py",
        "nadam.py",
        "optimizer.py",
        "rmsprop.py",
        "sgd.py",
    ],
    srcs_version = "PY3",
    deps = [
        "//:expect_tensorflow_installed",
        "//keras:backend",
        "//keras/initializers",
        "//keras/optimizers/optimizer_v2",
        "//keras/optimizers/schedules:learning_rate_schedule",
    ],
)

distribute_py_test(
    name = "optimizer_test",
    size = "medium",
    srcs = ["optimizer_test.py"],
    shard_count = 8,
    tags = [
        "multi_gpu",
        "no_windows",
        "nomultivm",  # TODO(b/203558991): Re-enable.
    ],
    deps = [
        "//:expect_absl_installed",
        "//:expect_tensorflow_installed",
        "//keras",
        "//keras/optimizers",
        "//keras/testing_infra:test_combinations",
    ],
)

# TODO(b/228209527): Combine this test with optimizer_test after
# fixing the NCCL issue.
distribute_py_test(
    name = "optimizer_pss_test",
    size = "medium",
    srcs = ["optimizer_pss_test.py"],
    shard_count = 8,
    tags = [
        "multi_gpu",
        "no_oss",
        "no_windows",
    ],
    deps = [
        "//:expect_absl_installed",
        "//:expect_tensorflow_installed",
        "//keras",
        "//keras/optimizers",
        "//keras/testing_infra:test_combinations",
    ],
)
