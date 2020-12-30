CMAKE_MINIMUM_REQUIRED(VERSION 3.15.0)
project(cnpy C CXX)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC")

# Set the RPATH config
# --------------------
# use, i.e. don't skip the full RPATH for the build tree
set(CMAKE_SKIP_BUILD_RPATH  FALSE)
# when building, use the install RPATH already
# (automated test will need this)
set(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)
# the RPATH to be used when installing
set(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib")

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

add_library(${PROJECT_NAME} SHARED "cnpy.cpp")
target_link_libraries(${PROJECT_NAME} PUBLIC CONAN_PKG::zlib)

install(TARGETS "cnpy" LIBRARY DESTINATION lib)
install(FILES "cnpy.h" DESTINATION include)

add_executable(example1 example1.cpp)
target_link_libraries(example1 ${PROJECT_NAME})
target_link_libraries(example1 CONAN_PKG::gtest)
install(TARGETS example1 DESTINATION bin)