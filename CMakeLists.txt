cmake_minimum_required(VERSION 3.4)
set(CMAKE_CXX_STANDARD 11)

project(solver)

add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/solver_application/equation.cpp)

include_directories(
${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib
${CMAKE_CURRENT_SOURCE_DIR}/solver_lib)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib formatter_ex)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/solver_lib solver_lib)

target_link_libraries(solver formatter_ex solver_lib)

install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin)

set(CPACK_SOURCE_GENERATOR "TGZ;ZIP")

set(CPACK_GENERATOR "RPM")

set(CPACK_DEBIAN_PACKAGE_MAINTAINER "the-blind-pew")
set(CPACK_GENERATOR "DEB")

set(WINDOWS_STORE TRUE)
set(CPACK_GENERATOR "WIX")

set(MACOSX_BUNDLE TRUE)
set(CPACK_GENERATOR "DragNDrop")

include(CPack)

unset(CPACK_GENERATOR_RPM CACHE)
unset(CPACK_GENERATOR_DEB CACHE)
unset(CPACK_GENERATOR_MSI CACHE)
unset(CPACK_GENERATOR_DMG CACHE)
