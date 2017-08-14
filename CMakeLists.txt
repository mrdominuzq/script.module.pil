project(inputstream.mpd)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(PkgConfig)
find_package(Kodi REQUIRED)
find_package(p8-platform REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(ZLIB REQUIRED)
find_package(PILLOW REQUIRED)

list(APPEND DEPLIBS ${p8-platform_LIBRARIES})

include_directories(${INCLUDES}
                    ${OPENSSL_INCLUDE_DIR}
                    ${ZLIB_INCLUDE_DIRS}
                    ${KODI_INCLUDE_DIR}/..) # Hack way with "/..", need bigger Kodi cmake rework to match right include ways (becomes done in future)
                    
list(APPEND DEPLIBS ${PILLOW_LIBRARIES} ${OPENSSL_LIBRARIES} ${ZLIB_LIBRARIES})

build_addon(script.module.pil PILLOW DEPLIBS)

include(CPack)
