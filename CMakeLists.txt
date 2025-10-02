cmake_minimum_required(VERSION 3.14)

project(STC3115GenericDriver
    VERSION 1.0.0
    DESCRIPTION "Generic C driver for the STC3115 gas gauge"
    LANGUAGES C
)

# Library target built from the core driver sources in src/
add_library(STC3115GenericDriver STATIC
    src/stc3115_Driver.c
    src/stc3115_I2C.c
)

# Public include directory so consumers can #include the headers from src/
target_include_directories(STC3115GenericDriver
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/src>
        $<INSTALL_INTERFACE:include>
)

# Reasonable defaults for C projects
set_target_properties(STC3115GenericDriver PROPERTIES
    C_STANDARD 99
    C_STANDARD_REQUIRED YES
    POSITION_INDEPENDENT_CODE ON
)

# Provide a convenient namespaced alias for consumers
add_library(STC3115::Driver ALIAS STC3115GenericDriver)

# Usage (FetchContent example):
#
# include(FetchContent)
# FetchContent_Declare(
#   STC3115GenericDriver
#   GIT_REPOSITORY https://github.com/<user>/STC3115GenericDriver.git
#   GIT_TAG        <commit-or-tag>
# )
# FetchContent_MakeAvailable(STC3115GenericDriver)
#
# target_link_libraries(your_app PRIVATE STC3115::Driver)
