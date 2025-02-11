cmake_minimum_required(VERSION 3.10)
project(rkllm_demo)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(SOURCE_FILES_1 src/llm_demo.cpp)
add_executable(llm_demo ${SOURCE_FILES_1})

set(SOURCE_FILES_2 src/multimodel_demo.cpp)
add_executable(multimodel_demo ${SOURCE_FILES_2})

include_directories(/usr/local/include)
set(RKLLM_RT_LIB /usr/lib/librkllmrt.so)
target_link_libraries(llm_demo  ${RKLLM_RT_LIB})
target_link_libraries(multimodel_demo  ${RKLLM_RT_LIB})


