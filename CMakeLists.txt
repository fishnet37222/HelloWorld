cmake_minimum_required (VERSION 3.8)

project ("HelloWorld")

set(CMAKE_CXX_STANDARD 17)

add_executable (HelloWorld WIN32 "App.h" "App.cpp" "PCH.h" "MainWindow.h" "MainWindow.cpp")

find_package(wxWidgets REQUIRED net gl core base webview)
include(${wxWidgets_USE_FILE})
target_compile_definitions(HelloWorld PRIVATE WX_USING_DLL)
target_link_libraries(HelloWorld ${wxWidgets_LIBRARIES})

find_package(Boost REQUIRED filesystem)
target_include_directories(HelloWorld PRIVATE ${Boost_INCLUDE_DIRS})
target_link_libraries(HelloWorld ${Boost_LIBRARIES})

target_precompile_headers(HelloWorld PRIVATE PCH.h)
