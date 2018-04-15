# Copyright (c) 2018, Ruslan Baratov
# All rights reserved.

cmake_minimum_required(VERSION 3.3)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.20.40.tar.gz"
    SHA1 "a500979296b4b6b1542a2881151ceb9c984f3e36"
)

project(android_google_apis_intel_x86_atom_system_image_packer)

hunter_add_package(android_sdk_packer)

# android_sdk_packer_unified_install
find_package(android_sdk_packer CONFIG REQUIRED)

hunter_add_package(Android-Google-APIs-Intel-x86-Atom-System-Image)
android_sdk_packer_parse_version_revision(
    FULL "${HUNTER_Android-Google-APIs-Intel-x86-Atom-System-Image_VERSION}"
    VERSION version
    REVISION revision
)

file(GLOB x "${ANDROID-GOOGLE-APIS-INTEL-X86-ATOM-SYSTEM-IMAGE_ROOT}/*")
android_sdk_packer_unified_install(
    OBJECTS ${x}
    DESTINATION "system-images/android-${version}/google_apis/x86"
)
