#include and src file
file(GLOB_RECURSE tinyxml_files_h *.h)
file(GLOB_RECURSE tinyxml_files_cpp *.cpp)

list(REMOVE_ITEM tinyxml_files_cpp *test.cpp)

#set(tinyxml_SRC
#        tinystr.cpp
#        tinystr.h
#        tinyxml.cpp
#        tinyxml.h
#        tinyxmlerror.cpp
#        tinyxmlparser.cpp)

add_library(tinyxml ${tinyxml_files_h} ${tinyxml_files_cpp})

#add_library(tinyxml OBJECT ${tinyxml_SRC})

#lib output
if (CMAKE_HOST_WIN32)
    INSTALL(TARGETS tinyxml DESTINATION lib)
elseif (CMAKE_HOST_APPLE)
    INSTALL(TARGETS tinyxml DESTINATION lib)
elseif (CMAKE_HOST_UNIX)
    INSTALL(TARGETS tinyxml DESTINATION lib)
endif ()

#install
#INSTALL(DIRECTORY . DESTINATION include FILES_MATCHING PATTERN "*.h")
INSTALL(FILES ${tinyxml_files_h}
        DESTINATION include)
#add_custom_target(install_tinyxml
#        "${CMAKE_COMMAND}" --build "${CMAKE_BINARY_DIR}" --target install
#        DEPENDS tinyxml
#        COMMENT "Installing tinyxml")
