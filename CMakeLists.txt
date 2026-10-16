add_library(s7 STATIC s7.c)
set_target_properties(s7 PROPERTIES C_STANDARD 11 C_STANDARD_REQUIRED ON C_EXTENSIONS ON)
if(WIN32)
    # s7's GCC/Clang detection otherwise enables the POSIX dynamic loader.
    target_compile_definitions(s7 PRIVATE WITH_C_LOADER=0)
else()
    target_link_libraries(s7 PUBLIC ${CMAKE_DL_LIBS} m)
endif()
