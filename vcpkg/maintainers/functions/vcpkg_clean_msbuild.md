---
title: vcpkg_clean_msbuild
description: Use vcpkg_clean_msbuild to remove MSBuild intermediate files.
ms.date: 11/30/2022
---
# vcpkg_clean_msbuild

> ![WARNING]
> This function has been deprecated in favor of [`vcpkg_msbuild_install`](vcpkg_msbuild_install.md).

Clean intermediate files generated by `vcpkg_install_msbuild()`.

## Usage

```cmake
vcpkg_clean_msbuild()
```

## Source

[scripts/cmake/vcpkg\_clean\_msbuild.cmake](https://github.com/Microsoft/vcpkg/blob/master/scripts/cmake/vcpkg_clean_msbuild.cmake)