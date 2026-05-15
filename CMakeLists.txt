# For more information about build system see
# https://docs.espressif.com/projects/esp-idf/en/latest/api-guides/build-system.html
# The following five lines of boilerplate have to be in your project's
# CMakeLists in this exact order for cmake to work correctly

cmake_minimum_required(VERSION 3.10)

# The Espressif IoT Development Framework (IDF) is required:
if(NOT DEFINED ENV{IDF_PATH})
  message(FATAL_ERROR "No Espressif IoT Development Framework found. Please set the environment variable IDF_PATH.\nYou may clone git@github.com:espressif/esp-idf.git and point IDF_PATH to there.")
endif()

if(NOT DEFINED ENV{IDF_TARGET})
  message(WARNING "ESP variant not set. grep \"idf_targets = \" $ENV{IDF_PATH}/docs/conf_common.py to see possible variants.")
endif()

include($ENV{IDF_PATH}/tools/cmake/project.cmake)
project(usb_host_arduino)
