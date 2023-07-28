cmake_minimum_required(VERSION 3.26...3.26)

# Project name and a few useful settings. Other commands can pick up the results
project("AudioFFT"
	VERSION 0.9.0
	DESCRIPTION "AudioFFT provides real-to-complex/complex-to-real FFT routines."
	LANGUAGES CXX
)

#Generate the static library from the library sources
add_library(audiofft STATIC "src/AudioFFT.cpp")

target_include_directories(audiofft PUBLIC "${PROJECT_SOURCE_DIR}/include")

option(BUILD_TEST "Build test" OFF)
if(BUILD_TEST)
    message(STATUS "Building AudioFFT Test...")
	add_executable(AudioFFT_Test "test/Test.cpp")
	target_link_libraries(AudioFFT_Test PRIVATE audiofft)
endif()
