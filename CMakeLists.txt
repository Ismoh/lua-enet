cmake_minimum_required(VERSION 3.20)

project(lua-enet)

add_library(enet SHARED enet.c)

set(LUA_LIBRARIES
D:/______BACKUP/NoitaMP_repo/NoitaMP/LuaJIT-2.1.0-beta3/bin/lua5.1.lib
)

set(LUA_INCLUDE_DIR
D:/______BACKUP/NoitaMP_repo/NoitaMP/LuaJIT-2.1.0-beta3/include
)
#find_package(Lua51 REQUIRED)

target_link_libraries(enet
    PRIVATE winmm ws2_32 ${LUA_LIBRARIES}
)

target_include_directories(enet
    PRIVATE ${LUA_INCLUDE_DIR}
)