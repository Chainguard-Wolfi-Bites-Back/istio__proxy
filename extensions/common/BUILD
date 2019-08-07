# Copyright 2019 Istio Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################
#

licenses(["notice"])

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_cc_test",
    "envoy_package",
)

envoy_package()

envoy_cc_library(
    name = "context",
    srcs = [
        "context.cc",
    ],
    hdrs = [
        "context.h",
    ],
    repository = "@envoy",
    visibility = ["//visibility:public"],
    deps = [
        ":node_info_cc_proto",
        "@com_google_protobuf//:protobuf",
        "@envoy//source/extensions/common/wasm/null:null_lib",
    ],
)

cc_proto_library(
    name = "node_info_cc_proto",
    visibility = ["//visibility:public"],
    deps = ["node_info_proto"],
)

proto_library(
    name = "node_info_proto",
    srcs = ["node_info.proto"],
)

envoy_cc_test(
    name = "context_test",
    size = "small",
    srcs = ["context_test.cc"],
    repository = "@envoy",
    deps = [
        ":context",
        "@envoy//source/extensions/common/wasm:wasm_lib",
    ],
)