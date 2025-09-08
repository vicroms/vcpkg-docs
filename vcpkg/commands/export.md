---
title: vcpkg export
description: Command line reference for the vcpkg export command. Create standalone SDK bundles.
ms.date: 08/21/2025
---
# vcpkg export

## Synopsis

```no-highlight
vcpkg export [options] {<package>... | --x-all-installed}
```

## Description

Exports built packages from the [installed directory](common-options.md#install-root) into a standalone developer SDK.

`export` produces a standalone, distributable SDK (Software Development Kit) that can be used on another machine without separately acquiring vcpkg. It contains:

1. The prebuilt binaries for the selected packages
1. Their transitive dependencies
1. [Integration files](#standard-integration), such as a [CMake toolchain][cmake] or [MSBuild props/targets][msbuild]

>[!NOTE]
> This command's behavior is different in [Classic
> Mode](../concepts/classic-mode.md) and [Manifest
> Mode](../concepts/manifest-mode.md)

The `export` command does not install any packages or transitive dependencies. It only exports packages that are already installed.

Refer to [Manifest Mode](export.md#Manifest-Mode) or [Classic Mode](export.md#Classic-Mode) for more details.

## <a name="Classic-Mode"></a>Classic Mode

In classic mode, `vcpkg export` accepts [triplet-qualified package specification](install.md#package-syntax) arguments (for example: `zlib:x64-windows`)

You specify packages to export by adding `<port name>:<triplet>` arguments to the command line.

For example, to export the `sqlite` package for `x64-windows` and `x64-linux`, use:

```no-highlight
vcpkg export sqlite:x64-windows sqlite:x64-linux --zip
```

This command exports the specified packages in zip format. Both `sqlite:x64-windows` and `sqlite:x64-linux` must be installed prior to running `vcpkg export`.

## <a name="Manifest-Mode"></a>Manifest Mode

In manifest mode, the command exports all currently installed packages. The installation directory includes all the packages declared in the manifest (`vcpkg.json`) as well as their transitive dependencies. Run `vcpkg install` before using this command to ensure that all required packages are installed.

In this mode you can't specify individual packages to export. The command operates on the entire installed state as a single entity, respecting the dependencies and versions specified in the manifest file.

Another difference is the requirement of the `--output-dir` option. This option specifies the directory where the exported packages will be stored.

For example, from the manifest directory

```no-highlight
vcpkg export --zip --output-dir=.\exports
```

Exports all currently installed packages to the `.\exports` directory in a zip file. The `--zip` option specifies that the exported packages should be compressed into a zip file.

### Standard Integration

Most export formats contain a standard set of integration files:

- A [CMake toolchain][cmake] at `/scripts/buildsystems/vcpkg.cmake`
- [MSBuild props/targets][msbuild] at `/scripts/buildsystems/msbuild/vcpkg.props` and `/scripts/buildsystems/msbuild/vcpkg.targets`
- The [installation tree][installation] at `/`

Some export formats differ from this standard set; see the individual format help below for more details.

### Formats

Officially supported SDK formats:

- [Raw Directory](#raw-directory)
- [Zip](#zip)
- [7zip](#7zip)
- [NuGet](#nuget)

#### Raw Directory

```no-highlight
vcpkg export --raw [options] <package>...
```

Create an uncompressed directory layout at `<output-dir>/<output>/`.

Contains the [Standard Integration Files][].

#### Zip

```no-highlight
vcpkg export --zip [options] <package>...
```

Create a zip compressed directory layout at `<output-dir>/<output>.zip`.

Contains the [Standard Integration Files][].

#### 7Zip

```no-highlight
vcpkg export --7zip [options] <package>...
```

Create a 7zip directory layout at `<output-dir>/<output>.7z`.

Contains the [Standard Integration Files][].

#### NuGet

```no-highlight
vcpkg export --nuget [options] <package>...
```

Create an [NuGet](/nuget/what-is-nuget) package at `<output-dir>/<nuget-id>.<nuget-version>.nupkg`.

Contains the [Standard Integration Files][] as well as additional MSBuild integration to support inclusion in an MSBuild C++ project (`.vcxproj`) via the NuGet Package Manager. Note that you cannot mix multiple NuGet packages produced with `export` together -- only one of the packages will be used. To add additional libraries, you must create a new export with the full set of dependencies.

Format specific options:

- [`--nuget-id`](#nuget-id)
- [`--nuget-version`](#nuget-version)
- [`--nuget-description`](#nuget-description)

#### IFW

<a id="ifw-configuration-file-path"></a>
<a id="ifw-installer-file-path"></a>
<a id="ifw-packages-directory-path"></a>
<a id="ifw-repository-directory-path"></a>
<a id="ifw-repository-url"></a>

IFW export has been removed.

#### Chocolatey

<a id="maintainer"></a>
<a id="version-suffix"></a>

Chocolatey export has been removed.

#### Prefab

<a id="prefab-artifact-id"></a>
<a id="prefab-group-id"></a>
<a id="prefab-maven"></a>
<a id="prefab-min-sdk"></a>
<a id="prefab-target-sdk"></a>
<a id="prefab-version"></a>

Prefab export has been removed.

## Options

All vcpkg commands support a set of [common options](common-options.md).

### `<package>`

This is the list of top-level built packages which will be included in the SDK. Any dependencies of these packages will also be included to ensure the resulting SDK is self-contained.

<a id="package-syntax"></a>

**Package Syntax**

```
<port name>:<triplet>
```

Package references without a triplet are automatically qualified by the [default target triplet](common-options.md#triplet).
Note: `<port name>:<triplet>` arguments are not allowed when using `vcpkg export` in manifest mode.

<a id="all-installed"></a>

### `--x-all-installed`

[!INCLUDE [experimental](../../includes/experimental.md)]

Export all installed packages. This option is implied when using `vcpkg export` in manifest mode.

<a id="dereference-symlinks"></a>

### `--dereference-symlinks`

Copies symlinks as regular files and directories in the exported results.

<a id="dry-run"></a>

### `--dry-run`

Do not perform the export, only print the export plan.

<a id="nuget-description"></a>

### `--nuget-description=`

Specifies the output description for [NuGet](#nuget) .nupkg files.

Defaults to "Vcpkg NuGet export".

<a id="nuget-id"></a>

### `--nuget-id=`

Specifies the output id for [NuGet](#nuget) .nupkg files.

This option overrides the [`--output`](#output) option specifically for the NuGet exporter. See `--output` for default values.

<a id="nuget-version"></a>

### `--nuget-version=`

Specifies the output version for [NuGet](#nuget) .nupkg files.

Defaults to `1.0.0`.

<a id="output"></a>

### `--output=`

Specifies the output base name.

Each SDK type uses this base name to determine its specific output files. See the SDK-specific documentation above for details.

Defaults to `vcpkg-export-<date>-<time>`. Scripted use of `export` should always pass this flag to ensure deterministic output.

<a id="output-dir"></a>

### `--output-dir=`

Specifies the output directory.

All top-level SDK files will be produced into this directory. This option is required in manifest mode. In classic mode, this is optional and defaults to the [vcpkg root directory](../users/config-environment.md#vcpkg_root).

[cmake]: ../users/buildsystems/cmake-integration.md
[msbuild]: ../users/buildsystems/msbuild-integration.md
[Standard Integration Files]: #standard-integration
[installation]: ../reference/installation-tree-layout.md
