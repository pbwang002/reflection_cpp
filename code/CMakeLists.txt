add_library(MyTestObjs OBJECT)
add_library(MyTestLink INTERFACE)

file(GLOB_RECURSE SRC_LIST ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
target_sources(MyTestObjs PRIVATE  ${SRC_LIST})

set(MyTestDepencyLibraries
    pthread
)

add_executable(MyTest)
target_link_libraries(MyTest PRIVATE $<BUILD_INTERFACE:MyTestLink> MyTestObjs ${MyTestDepencyLibraries})
set_target_properties(MyTest PROPERTIES RUNTIME_OUTPUT_NAME MyTest)
