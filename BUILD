load("//tools/bzl:plugin.bzl", "gerrit_plugin")

gerrit_plugin(
    name = "out-of-the-box",
    srcs = glob(["src/main/java/**/*.java"]),
    resources = glob(["src/main/resources/**/*"]),
    manifest_entries = [
        "Gerrit-PluginName: out-of-the-box",
        "Implementation-Title: Out of the box redirection",
        "Implementation-URL: https://github.com/GerritForge/out-of-the-box",
    ],
)
