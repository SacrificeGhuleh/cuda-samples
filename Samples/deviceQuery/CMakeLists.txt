project(cudaDeviceQuery LANGUAGES CUDA CXX)

add_executable(${PROJECT_NAME}
               deviceQuery.cpp)

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_LIST_DIR} ${CMAKE_CUDA_TOOLKIT_INCLUDE_DIRECTORIES})

target_link_libraries(${PROJECT_NAME} PUBLIC cuda-samples-common)
