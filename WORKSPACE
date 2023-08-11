workspace(name = "reverb")

# To change to a version of protoc compatible with tensorflow:
#  1. Convert the required header version to a version string, e.g.:
#     3011004 => "3.11.4"
#  2. Calculate the sha256 of the binary:
#     PROTOC_VERSION="3.11.4"
#     curl -L "https://github.com/protocolbuffers/protobuf/releases/download/v${PROTOC_VERSION}/protoc-${PROTOC_VERSION}-linux-x86_64.zip" | sha256sum
#  3. Update the two variables below.
#
PROTOC_VERSION = "21.9"
PROTOC_SHA256 = "d935f396a05cb02d4a1338db181c78f47884466a9f57d5ed4b7a4811816b69cf"

load(
    "//reverb/cc/platform/default:repo.bzl",
    "absl_deps",
    "cc_tf_configure",
    "github_apple_deps",
    "github_grpc_deps",
    "googletest_deps",
    "protoc_deps",
    "python_deps",
)

googletest_deps()

absl_deps()

# Note that the Python dependencies are not tracked by bazel here, but
# in setup.py.

github_apple_deps()

## Begin GRPC related deps
github_grpc_deps()

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")

grpc_deps()

load("@com_github_grpc_grpc//bazel:grpc_extra_deps.bzl", "grpc_extra_deps")

grpc_extra_deps()


load("@upb//bazel:workspace_deps.bzl", "upb_deps")

upb_deps()

load(
    "@build_bazel_rules_apple//apple:repositories.bzl",
    "apple_rules_dependencies",
)

apple_rules_dependencies()

load(
    "@build_bazel_apple_support//lib:repositories.bzl",
    "apple_support_dependencies",
)

apple_support_dependencies()
## End GRPC related deps


cc_tf_configure()

python_deps()

protoc_deps(version = PROTOC_VERSION, sha256 = PROTOC_SHA256)
