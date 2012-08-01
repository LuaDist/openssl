# Copyright (C) 2007-2012 LuaDist.
# Submitted by David Manura
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( openssl C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )

add_definitions ( -DOPENSSL_NO_ASM )
if ( WIN32 AND NOT CYGWIN )
  add_definitions ( -DOPENSSL_SYSNAME_WIN32 )
  add_definitions ( -DWIN32_LEAN_AND_MEAN )
  # avoid conflict: ocsp.h and wincrypt.h
  add_definitions ( -D_WINDLL )
  # build shared library symbols
endif ( )

if ( MINGW )
  set ( CMAKE_SHARED_LINKER_FLAGS "-Wl,--export-all" )
endif ( )

add_subdirectory ( crypto )
add_subdirectory ( ssl )
add_subdirectory ( apps )

install_header ( e_os2.h INTO openssl )
install_data ( tools/c_hash tools/c_info tools/c_issuer tools/c_name )
#programs
install_foo ( tools/c_rehash )
# programs
install_doc ( doc/ )
install_data ( FAQ LICENSE PROBLEMS README README.ASN1 README.ENGINE )

#~2DO: man pages
#~2DO: libcrypto.pc libssl.pc openssl.pc
#~2DO: demos?
#~2DO: tests
