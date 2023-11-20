cmake_minimum_required(VERSION 3.20)

project(lua-enet)

add_library(enet SHARED enet.c)

set(LUA_LIBRARIES
    ${PROJECT_SOURCE_DIR}/luajit2.1/bin/lua51.lib
)

set(ENET_LIBRARY
    ${PROJECT_SOURCE_DIR}/enet/enet.lib
)

set(LUA_INCLUDE_DIR
    ${PROJECT_SOURCE_DIR}/luajit2.1/include
)
set(ENET_INCLUDE_DIR
    ${PROJECT_SOURCE_DIR}/enet
)

include_directories(${ENET_INCLUDE_DIR})

target_link_libraries(enet
    PRIVATE winmm ws2_32 ${LUA_LIBRARIES} ${ENET_LIBRARY}
)

target_include_directories(enet
    PRIVATE ${ENET_INCLUDE_DIR}
    PRIVATE ${LUA_INCLUDE_DIR}
)