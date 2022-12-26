cmake_minimum_required(VERSION 3.16)

file(GLOB SOURCE 
	"../ref_gl/*.c"
	"../win32/glw_imp.c"
	"../game/q_shared.c"
	"../win32/q_shwin.c"
	"../win32/qgl_win.c"
	"../ref_gl/*.h"
	"../win32/glw_win.h"
	"../game/q_shared.h"
	"../qcommon/qcommon.h"
	"../qcommon/qfiles.h"
	"../client/ref.h"
	"../win32/winquake.h")

add_library(ref_gl SHARED ${SOURCE} ref_gl.def)
target_link_libraries(ref_gl winmm.lib)