add_library(ucd
  src/case.c
  src/categories.c
  src/ctype.c
  src/proplist.c
  src/scripts.c
  src/tostring.c
)
target_include_directories(ucd PUBLIC src/include)
# A shared build on Windows exports nothing without annotations, and espeak-ng links these symbols.
if(WIN32)
  set_target_properties(ucd PROPERTIES WINDOWS_EXPORT_ALL_SYMBOLS ON)
endif()

install(TARGETS ucd)
