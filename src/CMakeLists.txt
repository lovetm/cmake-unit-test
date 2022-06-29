include_directories(.)

file(GLOB files *.cpp **/*.cpp)

list(APPEND libs "")

foreach(file ${files})
  get_filename_component(name ${file} NAME_WLE)
  add_library(${name} ${file})
  list(APPEND libs ${name})
endforeach()

set(libs
    ${libs}
    CACHE INTERNAL "")
