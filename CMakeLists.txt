# Copyright (C) 2007-2009 LuaDist.
# Submitted by David Manura
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project(openssl C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
INCLUDE(dist.cmake)

if (WIN32 AND NOT CYGWIN)
   add_definitions(-DOPENSSL_SYSNAME_WIN32)
   add_definitions(-DWIN32_LEAN_AND_MEAN) # avoid conflict: ocsp.h and wincrypt.h
   add_definitions(-D_WINDLL) # build shared library symbols
endif(WIN32 AND NOT CYGWIN)

add_subdirectory(crypto)

add_subdirectory(ssl)

add_subdirectory(apps)

install(FILES e_os2.h DESTINATION ${INSTALL_INC}/openssl)
install(PROGRAMS tools/c_hash tools/c_info tools/c_issuer tools/c_name
        DESTINATION ${INSTALL_DATA})
install(PROGRAMS tools/c_rehash DESTINATION ${INSTALL_BIN})
install(DIRECTORY doc DESTINATION ${INSTALL_DOC})
install(FILES FAQ LICENSE PROBLEMS README README.ASN1 README.ENGINE
        DESTINATION ${INSTALL_DATA})

#~2DO: man pages
#~2DO: libcrypto.pc libssl.pc openssl.pc
#~2DO: demos?
#~2DO: tests




