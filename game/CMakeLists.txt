cmake_minimum_required(VERSION 3.16)

file(GLOB SOURCE 
	"../game/*.c"
	"../game/*.h")

add_library(gamex86 SHARED ${SOURCE} game.def)