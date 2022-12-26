cmake_minimum_required(VERSION 3.16)

set(CMAKE_GENERATOR_PLATFORM Win32)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

project(Quake2)

add_definitions(-D_DEBUG)
add_definitions(-DWIN32)
add_definitions(-D_WINDOWS)

add_compile_definitions(USE_MFC=0)
add_compile_definitions(Use_Debug_Libraries=1)
add_compile_definitions(Ignore_Export_Lib=0)

add_subdirectory(ref_gl)
add_subdirectory(game)

file(GLOB SOURCE 
	"./win32/cd_win.c"
	"./client/*.c"
	"./qcommon/cmd.c"
	"./qcommon/cmodel.c"
	"./qcommon/common.c"
	"./win32/conproc.c"
	"./qcommon/crc.c"
	"./qcommon/cvar.c"
	"./qcommon/files.c"
	"./win32/in_win.c"
	"./game/m_flash.c"
	"./qcommon/md4.c"
	"./qcommon/net_chan.c"
	"./win32/net_wins.c"
	"./qcommon/pmove.c"
	"./game/q_shared.c"
	"./win32/q_shwin.c"
	"./win32/snd_win.c"
	"./server/sv_ccmds.c"
	"./server/sv_ents.c"
	"./server/sv_game.c"
	"./server/sv_init.c"
	"./server/sv_main.c"
	"./server/sv_send.c"
	"./server/sv_user.c"
	"./server/sv_world.c"
	"./win32/sys_win.c"
	"./win32/vid_dll.c"
	"./win32/vid_menu.c"
	"./client/anorms.h"
	"./client/cdaudio.h"
	"./client/client.h"
	"./win32/conproc.h"
	"./client/console.h"
	"./game/game/h"
	"./client/input.h"
	"./client/keys.h"
	"./game/q_shared.h"
	"./qcommon/qcommon.h"
	"./qcommon/qfiles.h"
	"./client/qmenu.h"
	"./client/ref.h"
	"./client/screen.h"
	"./server/server.h"
	"./client/snd_loc.h"
	"./client/sound.h"
	"./client/vid.h"
	"./win32/winquake.h")

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT quake2)
set_property(DIRECTORY ${CMAKE_CURRENT_LIST_DIR} PROPERTY VS_DEBUGGER_WORKING_DIRECTORY quake2)

add_executable(quake2 WIN32 ${SOURCE} "./win32/q2.rc")
target_link_libraries(quake2 winmm.lib wsock32.lib)
