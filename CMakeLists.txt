cmake_minimum_required(VERSION 3.16)
project(cmake-storyboard-bug LANGUAGES CXX OBJC)

add_executable(${PROJECT_NAME}
	main.cpp
	main.m
	Main.storyboard
)
set_target_properties(${PROJECT_NAME} PROPERTIES MACOSX_BUNDLE ON)
target_link_libraries(${PROJECT_NAME} PRIVATE "-framework AppKit")

target_precompile_headers(${PROJECT_NAME} PRIVATE $<$<COMPILE_LANGUAGE:CXX>:<iostream$<ANGLE-R>>)
set_source_files_properties(Main.storyboard PROPERTIES MACOSX_PACKAGE_LOCATION "Resources")
