project(cudaMatrixMul LANGUAGES CUDA)

add_executable(${PROJECT_NAME} matrixMul.cu)

target_compile_options(${PROJECT_NAME} PRIVATE $<$<COMPILE_LANGUAGE:CUDA>:-gencode arch=compute_50,code=sm_50>)