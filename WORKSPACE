workspace(name = "org_tensorflow")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")


# Emscripten
http_archive(
 name = "emsdk",
 strip_prefix = "emsdk-3.1.10/bazel",
 url = "https://github.com/emscripten-core/emsdk/archive/3.1.10.tar.gz",
 sha256 = "3a207eed627366d9a7b31a634fa97c365cea0b6564b27e0cfadf7e53781606a3",
)


load("@emsdk//:deps.bzl", emsdk_deps = "deps")
emsdk_deps()


load("@emsdk//:emscripten_deps.bzl", emsdk_emscripten_deps = "emscripten_deps")
emsdk_emscripten_deps()


# Initialize the TensorFlow repository and all dependencies.
#
# The cascade of load() statements and tf_workspace?() calls works around the
# restriction that load() statements need to be at the top of .bzl files.
# E.g. we can not retrieve a new repository with http_archive and then load()
# a macro from that repository in the same file.
load("@//tensorflow:workspace3.bzl", "tf_workspace3")

tf_workspace3()

load("@//tensorflow:workspace2.bzl", "tf_workspace2")

tf_workspace2()

load("@//tensorflow:workspace1.bzl", "tf_workspace1")

tf_workspace1()

load("@//tensorflow:workspace0.bzl", "tf_workspace0")

tf_workspace0()
