project(script.module.pil)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(PkgConfig)
find_package(Kodi REQUIRED)
find_package(FreeType REQUIRED)
find_package(JPEG REQUIRED)
find_package(PNG REQUIRED)
find_package(ZLIB REQUIRED)
find_package(PILLOW REQUIRED)

include_directories(${INCLUDES}
                    ${PILLOW_INCLUDE_DIRS}
                    ${FREETYPE_INCLUDE_DIR}
                    ${JPEG_INCLUDE_DIR}
                    ${PNG_INCLUDE_DIR}
                    ${ZLIB_INCLUDE_DIRS}
                    ${KODI_INCLUDE_DIR})
                    
list(APPEND DEPLIBS ${PILLOW_LIBRARIES} ${FREETYPE_LIBRARIES} ${JPEG_LIBRARIES} ${PNG_LIBRARIES} ${ZLIB_LIBRARIES})

build_addon(script.module.pil PILLOW DEPLIBS)

include(CPack)
