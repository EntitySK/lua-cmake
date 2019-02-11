project(lua C)
cmake_minimum_required (VERSION 2.8)

set(SOURCE ${SOURCE}
  src/lbaselib.c
  src/ltm.c
  src/lutf8lib.c
  src/lzio.c
  src/lmem.c
  src/lparser.c
  src/lobject.c
  src/lbitlib.c
  src/lundump.c
  src/ltablib.c
  src/ldebug.c
  src/llex.c
  src/lctype.c
  src/ldblib.c
  src/ldo.c
  src/lfunc.c
  src/lapi.c
  src/lcorolib.c
  src/lcode.c
  src/ldump.c
  src/lmathlib.c
  src/lstate.c
  src/lvm.c
  src/loslib.c
  src/lstring.c
  src/ltable.c
  src/linit.c
  src/liolib.c
  src/loadlib.c
  src/lgc.c
  src/lopcodes.c
  src/lstrlib.c
  src/lauxlib.c
  )

set(SOURCE_LUA
  src/lua.c
  )

set(SOURCE_LUAC
  src/luac.c
  )

set(HEADERS ${HEADERS}
  src/llex.h
  src/lgc.h
  src/lobject.h
  src/lctype.h
  src/lzio.h
  src/ldo.h
  src/lua.h
  src/lapi.h
  src/lstate.h
  src/lstring.h
  src/ltm.h
  src/ltable.h
  src/lprefix.h
  src/lauxlib.h
  src/lopcodes.h
  src/lualib.h
  src/lcode.h
  src/lfunc.h
  src/lvm.h
  src/lmem.h
  src/luaconf.h
  src/lparser.h
  src/ldebug.h
  src/lua.hpp
  src/lundump.h
  src/llimits.h
  )

include_directories(src)

if(NOT WIN32)
  add_definitions(
    -DLUA_USE_POSIX
    -DLUA_USE_DLOPEN
    )
  set(DEPENDENCIES
    dl
    )
endif()

add_library(liblua STATIC ${SOURCE} ${HEADERS})
target_link_libraries(liblua ${DEPENDENCIES})

