# Build guide

F3D uses a CMake based build system, so building F3D just requires installing
needed dependencies, configuring and building.

## Dependencies

* [CMake](https://cmake.org) >= 3.1.
* [VTK](https://vtk.org) >= 9.0.0 (9.2.2 recommended).
* A C++17 compiler.
* A CMake-compatible build system (Visual Studio, XCode, Ninja, Make, etc.).
* Optionally, [Assimp](https://www.assimp.org/) >= 5.0.
* Optionally, Open CASCADE [OCCT](https://dev.opencascade.org/) >= 7.5.2.
* Optionally, [Alembic](http://www.alembic.io/) >= 1.7.
* Optionally, [Python](https://www.python.org/) >= 3.6 and [pybind11](https://github.com/pybind/pybind11) >= 2.2.
* Optionally, [Java](https://www.java.com) >= 18.

## VTK compatibility

As stated in the dependencies, F3D is compatible with VTK >= 9.0.0, however, many features are only available in certain conditions. We suggest using VTK 9.2.2 with RenderingRayTracing, RenderingExternal and IOExodus modules enabled in order to get as many features as possible in F3D.

## Configuration and building

Configure and generate the project with CMake,
then build the software using your build system.

Here is some CMake options of interest::
* `F3D_BUILD_APPLICATION`: Build the F3D executable.
* `F3D_INSTALL_SDK`: Install the F3D SDK for the [libf3d](../libf3d/README_LIBF3D.md).
* `BUILD_TESTING`: Enable the [tests](TESTING.md).
* `F3D_MACOS_BUNDLE`: On macOS, build a `.app` bundle.
* `F3D_WINDOWS_GUI`: On Windows, build a Win32 application (without console).
* `F3D_BUILD_WINDOWS_SHELL_THUMBNAILS_EXTENSION`: On Windows, build the shell thumbnails extension.
* `F3D_PLUGINS_STATIC_BUILD`: Build all plugins as static library (embedded into `libf3d`) and automatically loaded by the application.

Some modules, plugins and bindings depending on external libraries can be optionally enabled with the following CMake variables:

* `F3D_MODULE_RAYTRACING`: Support for raytracing rendering. Requires that VTK has been built with `OSPRay` and `VTK_MODULE_ENABLE_VTK_RenderingRayTracing` turned on. Disabled by default.
* `F3D_MODULE_EXTERNAL_RENDERING`: Support for external render window, Requires that VTK has been built with `VTK_MODULE_ENABLE_VTK_RenderingExternal` turned on. Disabled by default.
* `F3D_PLUGIN_BUILD_EXODUS`: Support for ExodusII (.ex2) file format. Requires that VTK has been built with `IOExodus` module (and `hdf5`). Enabled by default.
* `F3D_PLUGIN_BUILD_OCCT`: Support for STEP and IGES file formats. Requires `OpenCASCADE`. Disabled by default.
* `F3D_PLUGIN_BUILD_ASSIMP`: Support for FBX, DAE, OFF and DXF file formats. Requires `Assimp`. Disabled by default.
* `F3D_PLUGIN_BUILD_ALEMBIC`: Support for ABC file format. Requires `Alembic`. Disabled by default.
* `F3D_BINDINGS_PYTHON`: Generate python bindings (requires `Python` and `pybind11`). Disabled by default.
* `F3D_BINDINGS_JAVA`: Generate java bindings (requires `Java` and `JNI`). Disabled by default.