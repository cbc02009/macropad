#
# Add 3rd party libraries to cmake here so we don't have to modify their repositories
#
#

if( EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/SAMD21_DFP )

    message(STATUS "Found SAMD21 DFP")

    add_library( SAMD21_DFP INTERFACE IMPORTED GLOBAL)
    target_include_directories(
            SAMD21_DFP
            INTERFACE
            SAMD21_DFP/1.3.395/gcc
            SAMD21_DFP/1.3.395/gcc/gcc
            SAMD21_DFP/1.3.395/include
            SAMD21_DFP/1.3.395/include/component
            SAMD21_DFP/1.3.395/include/instance
            SAMD21_DFP/1.3.395/include/pio
    )

else()
    message(FATAL_ERROR "Could not find DFP!")
endif()

# CMSIS library
if ( EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/CMSIS )

    message(STATUS "Found external library: CMSIS")

    add_library( CMSIS INTERFACE IMPORTED GLOBAL )
    target_include_directories( CMSIS INTERFACE CMSIS/5.7/Core/Include)

else()
    message(FATAL_ERROR "Could not find CMSIS library!")
endif ()