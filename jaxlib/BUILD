# Copyright 2018 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# JAX is Autograd and XLA

load("@org_tensorflow//tensorflow/core:platform/default/build_config.bzl", "pyx_library")
load("@org_tensorflow//tensorflow:tensorflow.bzl", "tf_pybind_extension")

licenses(["notice"])  # Apache 2

package(default_visibility = ["//visibility:public"])

pyx_library(
    name = "lapack",
    srcs = ["lapack.pyx"],
    py_deps = ["@org_tensorflow//third_party/py/numpy"],
)

py_library(
    name = "jaxlib",
    srcs = ["version.py"],
)

tf_pybind_extension(
    name = "pytree",
    srcs = ["pytree.cc"],
    copts = [
        "-fexceptions",
        "-fno-strict-aliasing",
        "-Wno-c++98-c++11-compat",
    ],
    features = ["-use_header_modules"],
    module_name = "pytree",
    deps = [
        "@com_google_absl//absl/algorithm:container",
        "@com_google_absl//absl/container:flat_hash_map",
        "@com_google_absl//absl/hash",
        "@com_google_absl//absl/memory",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/strings:str_format",
        "@pybind11",
    ],
)
