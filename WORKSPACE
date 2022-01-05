load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# To update TensorFlow to a new revision,
# a) update URL and strip_prefix to the new git commit hash
# b) get the sha256 hash of the commit by running:
#    curl -L https://github.com/tensorflow/tensorflow/archive/<git hash>.tar.gz | sha256sum
#    and update the sha256 with the result.
http_archive(
    name = "org_tensorflow",
    sha256 = "e6e68270b7fb0dda26656f4985b3d118b5a9d3fa60433ced42ce2fc5676716d5",
    strip_prefix = "tensorflow-d9b47d5722fc08c5d06afba9f63177de266801f5",
    urls = [
        "https://github.com/tensorflow/tensorflow/archive/d9b47d5722fc08c5d06afba9f63177de266801f5.tar.gz",
    ],
)

load("@org_tensorflow//third_party:repo.bzl", "tf_http_archive")

tf_http_archive(
    name = "pybind11",
    urls = [
        "https://storage.googleapis.com/colesbury/pybind11/archive/v2.6.2-nogil.tar.gz",
        "https://github.com/colesbury/pybind11/archive/v2.6.2-nogil.tar.gz",
    ],
    sha256 = "258de86578becae9879245f03f28c3cfbb45e474e15f61c6a05a1940735e2032",
    strip_prefix = "pybind11-2.6.2-nogil",
    build_file = "//third_party:pybind11.BUILD",
    patch_file = "//third_party:pybind11.patch",
    system_build_file = "//third_party/systemlibs:pybind11.BUILD",
)

# For development, one can use a local TF repository instead.
# local_repository(
#    name = "org_tensorflow",
#    path = "tensorflow",
# )

load("//third_party/pocketfft:workspace.bzl", pocketfft = "repo")
pocketfft()

# Initialize TensorFlow's external dependencies.
load("@org_tensorflow//tensorflow:workspace3.bzl", "tf_workspace3")
tf_workspace3()

load("@org_tensorflow//tensorflow:workspace2.bzl", "tf_workspace2")
tf_workspace2()

load("@org_tensorflow//tensorflow:workspace1.bzl", "tf_workspace1")
tf_workspace1()

load("@org_tensorflow//tensorflow:workspace0.bzl", "tf_workspace0")
tf_workspace0()
