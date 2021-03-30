workspace(
    name = "tink_javascript",
    managed_directories = {"@npm": ["node_modules"]},
)

local_repository(
    name = "tink_base",
    path = "..",
)

local_repository(
    name = "tink_angular",
    path = "../third_party/angular",
)

load("@tink_base//:tink_base_deps.bzl", "tink_base_deps")
tink_base_deps()

load("@tink_base//:tink_base_deps_init.bzl", "tink_base_deps_init")
tink_base_deps_init()

load("@tink_javascript//:tink_javascript_deps.bzl", "tink_javascript_deps")
tink_javascript_deps()

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")
yarn_install(
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

load("@npm//@bazel/karma:package.bzl", "npm_bazel_karma_dependencies")
npm_bazel_karma_dependencies()

load("@io_bazel_rules_webtesting//web:repositories.bzl", "web_test_repositories")
web_test_repositories()

load("@io_bazel_rules_webtesting//web/versioned:browsers-0.3.2.bzl", "browser_repositories")
browser_repositories(
    chromium = True,
    firefox = True,
)

load("@io_bazel_rules_closure//closure:repositories.bzl", "rules_closure_dependencies", "rules_closure_toolchains")
rules_closure_dependencies()
rules_closure_toolchains()
