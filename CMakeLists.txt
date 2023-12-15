cmake_minimum_required(VERSION 3.20)

project(lua-enet
    VERSION 2.3.6
    HOMEPAGE_URL "https://github.com/Ismoh/lua-enet"
    DESCRIPTION "Lua bindings for zpl-c/eNet."
)

add_library(enet SHARED enet.c)

set(LUA_LIBRARIES ${PROJECT_SOURCE_DIR}/luajit2.1/bin/lua51.lib
    CACHE FILEPATH "Path to lua lib"
)

set(LUA_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/luajit2.1/include
    CACHE PATH "Path to lua include dir"
)
set(ENET_INCLUDE_DIR
    ${PROJECT_SOURCE_DIR}
)

include_directories(${ENET_INCLUDE_DIR})

target_link_libraries(enet
    PRIVATE winmm ws2_32 ${LUA_LIBRARIES}
)

target_include_directories(enet
    PRIVATE ${ENET_INCLUDE_DIR}
    PRIVATE ${LUA_INCLUDE_DIR}
)