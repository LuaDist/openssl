# Copyright (C) 2007-2012 LuaDist.
# Submitted by David Manura
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

include_directories ( ../crypto .. ../include )

add_definitions ( -DOPENSSL_BUILD_SHLIBSSL )
# for shared library

set ( LIBSRC s2_meth.c s2_srvr.c s2_clnt.c s2_lib.c s2_enc.c s2_pkt.c s3_meth.c s3_srvr.c 
  s3_clnt.c s3_lib.c s3_enc.c s3_pkt.c s3_both.c s23_meth.c s23_srvr.c s23_clnt.c 
  s23_lib.c s23_pkt.c t1_meth.c t1_srvr.c t1_clnt.c t1_lib.c t1_enc.c d1_meth.c d1_srvr.c 
  d1_clnt.c d1_lib.c d1_pkt.c d1_both.c d1_enc.c ssl_lib.c ssl_err2.c ssl_cert.c 
  ssl_sess.c ssl_ciph.c ssl_stat.c ssl_rsa.c ssl_asn1.c ssl_txt.c ssl_algs.c bio_ssl.c 
  ssl_err.c kssl.c t1_reneg.c )

add_library ( ssl ${LIBSRC} ssl.def )
target_link_libraries ( ssl crypto )

install_header ( ssl.h ssl2.h ssl3.h ssl23.h tls1.h dtls1.h kssl.h INTO openssl )
install_library ( ssl )
