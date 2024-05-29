cmake_minimum_required(VERSION 3.6)

project(mTCP VERSION 0.1.0 LANGUAGES C CXX ASM)
set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 98)

if(POLICY CMP0076)
    cmake_policy(SET CMP0076 NEW)
endif()

set(SRC_DIR .)
set(INC_DIR ${SRC_DIR}/INCLUDE/)
set(TCP_INC_DIR ${SRC_DIR}/TCPINC/)
set(TCP_LIB_DIR ${SRC_DIR}/TCPLIB/)

add_library(mTCP STATIC)

target_include_directories(mTCP PUBLIC ${INC_DIR})
target_sources(mTCP PUBLIC
        ${INC_DIR}irc.h
        ${INC_DIR}sntp.h
        ${INC_DIR}telnet.h
        ${INC_DIR}unicode.h
)
target_include_directories(mTCP PUBLIC ${TCP_INC_DIR})
target_sources(mTCP PUBLIC
        ${TCP_INC_DIR}arp.h
        ${TCP_INC_DIR}dns.h
        ${TCP_INC_DIR}eth.h
        ${TCP_INC_DIR}ethtype.h
        ${TCP_INC_DIR}inlines.h
        ${TCP_INC_DIR}ip.h
        ${TCP_INC_DIR}iptype.h
        ${TCP_INC_DIR}ipv6.h
        ${TCP_INC_DIR}packet.h
        ${TCP_INC_DIR}ringbuf.h
        ${TCP_INC_DIR}sntplib.h
        ${TCP_INC_DIR}tcp.h
        ${TCP_INC_DIR}tcpsockm.h
        ${TCP_INC_DIR}timer.h
        ${TCP_INC_DIR}trace.h
        ${TCP_INC_DIR}types.h
        ${TCP_INC_DIR}udp.h
        ${TCP_INC_DIR}utils.h
)
target_include_directories(mTCP PRIVATE ${TCP_LIB_DIR})
target_sources(mTCP PRIVATE
        ${TCP_LIB_DIR}arp.cpp
        ${TCP_LIB_DIR}dns.cpp
        ${TCP_LIB_DIR}eth.cpp
        ${TCP_LIB_DIR}ethtype.cpp
        ${TCP_LIB_DIR}ip.cpp
        ${TCP_LIB_DIR}ipasm.asm
        ${TCP_LIB_DIR}iptype.cpp
        ${TCP_LIB_DIR}packet.cpp
        ${TCP_LIB_DIR}sntplib.cpp
        ${TCP_LIB_DIR}tcp.cpp
        ${TCP_LIB_DIR}tcpsockm.cpp
        ${TCP_LIB_DIR}timer.cpp
        ${TCP_LIB_DIR}trace.cpp
        ${TCP_LIB_DIR}udp.cpp
        ${TCP_LIB_DIR}unicode.cpp
        ${TCP_LIB_DIR}utils.cpp
)
