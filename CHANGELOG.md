# Changelog

All notable changes to this fork are documented in this file.

This project is a fork of st-sw/STC3115GenericDriver (https://github.com/st-sw/STC3115GenericDriver) with build system improvements.

## [Released] / [1.0.2] - 2025-10-02

### Added
- CMake build system support
- FetchContent support for easy integration into CMake projects
- Installation targets for system-wide installation

### Fixed
- Forward declarations for static functions in src/stc3115_Driver.c to resolve compilation errors

## How to Use This Fork

### Usage (FetchContent example):
```cmake
include(FetchContent)
FetchContent_Declare(
  STC3115GenericDriver
  GIT_REPOSITORY https://github.com/sid-audioinventions/STC3115GenericDriver.git
  GIT_TAG        <commit-or-tag>
)
FetchContent_MakeAvailable(STC3115GenericDriver)

target_link_libraries(your_app PRIVATE STC3115::Driver)
