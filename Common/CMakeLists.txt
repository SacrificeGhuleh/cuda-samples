project(cuda-samples-common)

option(ENABLE_GL OFF)
option(ENABLE_DIRECT OFF)

# region INTERFACE
add_library(${PROJECT_NAME} INTERFACE)

target_include_directories(${PROJECT_NAME} INTERFACE ${CMAKE_CURRENT_LIST_DIR})

target_sources(${PROJECT_NAME} INTERFACE
               drvapi_error_string.h
               exception.h
               helper_cuda.h
               helper_cuda_drvapi.h
               helper_cusolver.h
               helper_functions.h
               helper_image.h
               helper_math.h
               helper_multiprocess.h
               helper_nvJPEG.hxx
               helper_string.h
               helper_timer.h
               nvrtc_helper.h)

if (ENABLE_GL)
  target_sources(${PROJECT_NAME} INTERFACE helper_gl.h)
endif ()

if (ENABLE_DIRECT)
  target_sources(${PROJECT_NAME} INTERFACE rendercheck_d3d11.h dynlink_d3d11.h)
endif ()

# endregion INTERFACE

# region OBJECTS
add_library(${PROJECT_NAME}_objects OBJECT)

target_sources(${PROJECT_NAME}_objects PRIVATE
               helper_multiprocess.cpp
               )


if (ENABLE_DIRECT)
  target_sources(${PROJECT_NAME} INTERFACE rendercheck_d3d11.cpp)
endif ()

target_link_libraries(${PROJECT_NAME}_objects PRIVATE ${PROJECT_NAME})

# endregion OBJECTS