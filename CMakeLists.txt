cmake_minimum_required(VERSION 3.20)

project(lua-enet)

add_library(enet SHARED enet.c)

set(LUA_LIBRARIES
    ${PROJECT_SOURCE_DIR}/luajit2.1/bin/lua51.lib
)

set(LUA_INCLUDE_DIR
    ${PROJECT_SOURCE_DIR}/luajit2.1/include
)

target_link_libraries(enet
    PRIVATE winmm ws2_32 ${LUA_LIBRARIES}
)

target_include_directories(enet
    PRIVATE ${LUA_INCLUDE_DIR}
    PRIVATE ${PROJECT_SOURCE_DIR}/enet # PRIVATE?
)