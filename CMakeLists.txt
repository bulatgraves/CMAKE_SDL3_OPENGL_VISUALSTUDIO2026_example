cmake_minimum_required (VERSION 3.10)

if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("CMakeProject")

add_executable (CMakeProject
"src/main.cpp"
"src/glad.c"
)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET CMakeProject PROPERTY CXX_STANDARD 20)
endif()

target_include_directories(CMakeProject PRIVATE
"${CMAKE_CURRENT_SOURCE_DIR}/SDL3/include"
"${CMAKE_CURRENT_SOURCE_DIR}/glad_include"
)

target_link_libraries(CMakeProject PUBLIC
"${CMAKE_CURRENT_SOURCE_DIR}/SDL3/lib/x64/SDL3.lib"
)