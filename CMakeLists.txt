cmake_minimum_required(VERSION "3.29.3" FATAL_ERROR)


# [[ Project ]]
# [[ ----------------------------------------------------------------------- ]]
# [[ ----------------------------------------------------------------------- ]]

project("Project"
	
    VERSION 0.0.1

    DESCRIPTION "Project description"

    LANGUAGES CXX)

set(EXECUTABLE_NAME "${PROJECT_NAME}")



set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# [[ ----------------------------------------------------------------------- ]]
# [[ ----------------------------------------------------------------------- ]]
# [[ Project ]]




# [[ Output Locations ]]
# [[ ----------------------------------------------------------------------- ]]
# [[ ----------------------------------------------------------------------- ]]

set(OUTPUT_DIRECTORY "")

set(CMAKE_BINARY_DIR "${CMAKE_SOURCE_DIR}/build/bin")



if(CMAKE_SIZEOF_VOID_P EQUAL 8)

    set(OUTPUT_DIRECTORY

        "${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/64-bit/")
endif()

if(CMAKE_SIZEOF_VOID_P EQUAL 4)

    set(OUTPUT_DIRECTORY

        "${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/32-bit/")
endif()



set(CMAKE_RUNTIME_OUTPUT_DIRECTORY	# Defines executable path
	
    "${OUTPUT_DIRECTORY}/$<CONFIG>/executable")

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY	# Defines shared lib path
	
    "${OUTPUT_DIRECTORY}/$<CONFIG>/executable")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY	# Defines static lib path
	
    "${OUTPUT_DIRECTORY}/$<CONFIG>/lib_static")

# [[ ----------------------------------------------------------------------- ]]
# [[ ----------------------------------------------------------------------- ]]
# [[ Output Locations ]]





# [[ Executable Target ]]
# [[ ----------------------------------------------------------------------- ]]
# [[ ----------------------------------------------------------------------- ]]

add_executable(${EXECUTABLE_NAME})



set(HEADER_FILES

    "${CMAKE_CURRENT_SOURCE_DIR}/include/factorial.hpp")

set(SOURCE_FILES

	"${CMAKE_CURRENT_SOURCE_DIR}/main.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/src/factorial.cpp")



target_sources(${EXECUTABLE_NAME}
	
    PUBLIC
    ${HEADER_FILES}

    PRIVATE
    ${SOURCE_FILES})



target_include_directories(${EXECUTABLE_NAME}

    PUBLIC
    "${CMAKE_CURRENT_SOURCE_DIR}/include/")

# [[ ----------------------------------------------------------------------- ]]
# [[ ----------------------------------------------------------------------- ]]
# [[ Executable Target ]]