set(TARGET QtMQTT)

find_package(Qt5 REQUIRED Core Network WebSockets)

FILE(GLOB_RECURSE SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/mqtt/*.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/mqtt/*.cpp)

add_library(${TARGET} STATIC ${SOURCES})

target_include_directories(${TARGET}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src/mqtt
        ${CMAKE_CURRENT_SOURCE_DIR}/src/mqtt/include/QtMqtt
        ${Qt5Core_PRIVATE_INCLUDE_DIRS}
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src/mqtt/include)

target_link_libraries(${TARGET}
    PUBLIC Qt5::Core Qt5::Network Qt5::WebSockets)