cmake_minimum_required(VERSION 3.5)

project(my_rpc)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(Boost REQUIRED)
find_package(Protobuf REQUIRED)

set(LIBMYRPC_SRC ./src/rpc_meta.pb.cc)
add_library(myrpc ${LIBMYRPC_SRC})

add_executable(server src/server.cpp)
target_link_libraries(server ${Boost_LIBRARIES} ${Protobuf_LIBRARIES} myrpc)

add_executable(client src/client.cpp)
target_link_libraries(client ${Boost_LIBRARIES} ${Protobuf_LIBRARIES} myrpc)
