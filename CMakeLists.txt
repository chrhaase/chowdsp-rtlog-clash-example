cmake_minimum_required(VERSION 3.25)
project(ChowDspRtLogClashExample VERSION 0.0.1)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_OSX_DEPLOYMENT_TARGET "11.0" CACHE STRING "Support macOS down to Big Sur" FORCE)
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

include(FetchContent)
FetchContent_Declare(juce GIT_REPOSITORY https://github.com/juce-framework/JUCE.git)
FetchContent_MakeAvailable(juce)

FetchContent_Declare(chowdsp GIT_REPOSITORY https://github.com/Chowdhury-DSP/chowdsp_utils.git)
FetchContent_MakeAvailable(chowdsp)

FetchContent_Declare(rtlog GIT_REPOSITORY https://github.com/cjappl/rtlog-cpp.git GIT_TAG main)
FetchContent_MakeAvailable(rtlog)

add_executable(ChowDspRtLogClashExample src/main.cpp)

target_link_libraries(ChowDspRtLogClashExample PRIVATE
    chowdsp::chowdsp_plugin_state
    rtlog)