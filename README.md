# PKGBUILD for building mediapipe python binding for ArchLinux with GPU support by opengl

Update: 2024.05.21, this PKGBUILD is tested for mediapipe 0.10.14, and should also works for the latest master branch.

To build mediapipe for ArchLinux with GPU support by opengl, we need to:

1. update rules_apple to version 3.2.1, as this [patch](./0001-update-rules_apple.patch) do.
2. disable unused patch, as this [patch](./0002-delete-unused-com_google_protobuf_fixes.diff.patch) do.
3. setup opencv4 headers. as this [patch](./0004-use-opencv4-headers.patch) do.
4. add `--experimental_allow_proto3_optional` to `protoc` command, as this [patch](0005-add-arg-experimental_allow_proto3_optional-to-protoc.patch) do.
5. set `link_opencv` to `True` in `setup.py` by find and replace.
6. optionally, set `__version__` in `setup.py` to the right release.
7. update `.bazelversion` to match the bazel version we are using. We use bazel 7.0.0 here.
8. build the wheel file with `MEDIAPIPE_DISABLE_GPU=0 python -m build --wheel --no-isolation`, or `MEDIAPIPE_DISABLE_GPU=0 python setup.py bdist_wheel`, or just use `extra-x86_64-build` to create the package for ArchLinux.

If you would like to build mediapipe with CUDA support, refer to this [repo](https://github.com/pydehon/mediapipe). You will need more modifications if you would like to build mediapipe != 0.10.1 with CUDA support for ArchLinux or other platform.

You could also refer to this [post](https://blog.csdn.net/qq_56548850/article/details/123981579) for building mediapipe for Nvidia Jetson Nano platform (zh-cn only).
