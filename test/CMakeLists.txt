include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip
)
FetchContent_MakeAvailable(googletest)

enable_testing()

include(GoogleTest)

include_directories(../src)

file(GLOB files *.test.cpp **/*.test.cpp)

foreach(file ${files})
  get_filename_component(name ${file} NAME_WLE)
  add_executable(${name} ${file})
  target_link_libraries(${name} ${libs} gtest_main)
  gtest_discover_tests(${name})
endforeach()
