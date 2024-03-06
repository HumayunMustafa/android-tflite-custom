cmake_minimum_required(VERSION 3.12)

project("android-tflite-custom")

#####################tflite dependencies##################
# This configuration is taken from  https://github.com/cuongvng/TF-Lite-Cpp-API-for-Android
set(INCLUDE_DIRS
        ${CMAKE_CURRENT_LIST_DIR}/tf-lite-api/include
        ${CMAKE_CURRENT_LIST_DIR}/tf-lite-api/include/flatbuffers/include
        )

include_directories(${INCLUDE_DIRS})

add_library(tflite SHARED IMPORTED)
set_target_properties(tflite PROPERTIES IMPORTED_LOCATION
        ${CMAKE_CURRENT_LIST_DIR}/tf-lite-api/generated-libs/${ANDROID_ABI}/libtensorflowlite.so
        )

#####################tflite dependencies###################

add_library(selfie-segmentation/selfie-segmentation.cc)

target_link_libraries(tflite)