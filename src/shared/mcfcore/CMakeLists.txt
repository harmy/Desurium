include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_SOURCE_DIR}/code
  ${GLOBAL_INCLUDE_DIRS}
  ${COMMON_INCLUDE_DIRS}
  ${COURGETTE_INCLUDE_DIRS}
  ${TINYXML_INCLUDE_DIRS}
)

file(GLOB Headers code/*.h)
file(GLOB Sources code/*.cpp
                  code/mcf/*.cpp
                  code/thread/*.cpp
)

if(DEFINED WIN32)
  file(GLOB PlattformSources)
else()
  file(GLOB PlattformSources)
endif()

add_library(mcfcore SHARED ${Sources} ${PlattformSources})
target_link_libraries(mcfcore
    tinyxml
)

install(TARGETS mcfcore
        DESTINATION "${LIB_INSTALL_DIR}")