cmake_minimum_required(VERSION 3.16)

file(GLOB SOURCE 
	"../ref_soft/*.c"
	"../game/q_shared.c"
	"../win32/q_shwin.c"
	"../win32/rw_ddraw.c"
	"../win32/rw_dib.c"
	"../win32/rw_imp.c"
	"../ref_soft/adivtab.h"
	"../ref_soft/anorms.h"
	"../game/q_shared.h"
	"../qcommon/qcommon.h"
	"../qcommon/qfiles.h"
	"../ref_soft/r_local.h"
	"../ref_soft/r_model.h"
	"../ref_soft/rand1k.h"
	"../client/ref.h"
	"../win32/rw_win.h"
	"../win32/winquake.h")

file(GLOB ASM_SOURCE
	"../ref_soft/*.asm")

set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} /SAFESEH:NO")

set_source_files_properties(${ASM_SOURCE} PROPERTIES COMPILE_FLAGS "/Cp")

add_library(ref_soft SHARED ${SOURCE} ${ASM_SOURCE} ref_soft.def)
target_link_libraries(ref_soft winmm.lib)
