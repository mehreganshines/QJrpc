Project(qjsonRPC)

set(CMAKE_VERBOSE_MAKEFILE ON)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
cmake_minimum_required(VERSION 3.6)
find_package(Qt5 COMPONENTS Core REQUIRED)
set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -std=c++0x")


include_directories(${Qt5Core_INCLUDE_DIRS})

## project main ##
set(TARGET ${CMAKE_PROJECT_NAME})
set(qj_src
        libQJsonRPC/Private/http-parser/http_parser.c
        libQJsonRPC/qjsonrpcabstractserver.cpp
        libQJsonRPC/qjsonrpchttpclient.cpp
        libQJsonRPC/qjsonrpchttpserver.cpp
        libQJsonRPC/qjsonrpchttpservermultithreaded.cpp
        libQJsonRPC/qjsonrpclocalserver.cpp
        libQJsonRPC/qjsonrpcmessage.cpp
        libQJsonRPC/qjsonrpcservice.cpp
        libQJsonRPC/qjsonrpcserviceprovider.cpp
        libQJsonRPC/qjsonrpcservicereply.cpp
        libQJsonRPC/qjsonrpcsocket.cpp
        libQJsonRPC/qjsonrpctcpserver.cpp
    PUBLIC_LIBRARIES
        Qt::Core
)
## headers ##


include_directories(${CMAKE_INCLUDE_CURRENT_DIR})

### to do
#set(PRIVATE_HEADERS
#    libQJsonRPC/Private/qjsonrpcservice_p.h
#    libQJsonRPC/Private/qjsonrpcsocket_p.h
#    libQJsonRPC/Private/qjsonrpcabstractserver_p.h
#    libQJsonRPC/Private/qjsonrpcservicereply_p.h
#    libQJsonRPC/Private/qjsonrpchttpserver_p.h
#    libQJsonRPC/Private/http-parser/http_parser.h
#    libQJsonRPC/Private/qjsonrpchttpservermultithreaded_p.h
#)

#set(HEADERS
#	libQJsonRPC/qjsonrpcmessage.h
#	libQJsonRPC/qjsonrpcservice.h
#	libQJsonRPC/qjsonrpcsocket.h
#	libQJsonRPC/qjsonrpcserviceprovider.h
#	libQJsonRPC/qjsonrpcabstractserver.h
#	libQJsonRPC/qjsonrpclocalserver.h
#	libQJsonRPC/qjsonrpctcpserver.h
#	libQJsonRPC/qjsonrpcglobal.h
#	libQJsonRPC/qjsonrpcservicereply.h
#	libQJsonRPC/qjsonrpchttpclient.h
#	libQJsonRPC/qjsonrpchttpserver.h
#	libQJsonRPC/qjsonrpchttpservermultithreaded.h
#)


## end

add_executable(qm2cm ${qj_src})
target_link_libraries(libQJsonRPC  ${Qt5Core_LIBRARIES})

