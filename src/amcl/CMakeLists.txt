add_subdirectory(map)
add_subdirectory(pf)
add_subdirectory(sensors)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(${CMAKE_CURRENT_PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${CMAKE_SOURCE_DIR}/include)

set(amcl_dependencies )

add_library(amcl ${amcl_map_src} ${amcl_pf_src} ${amcl_sensors_src})
target_link_libraries(amcl ${amcl_dependencies})
if (${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
  target_compile_definitions(amcl PUBLIC HAVE_DRAND48)
endif ()
