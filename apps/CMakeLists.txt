# Copyright (C) 2007-2012 LuaDist.
# Submitted by David Manura
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

include_directories ( .. ../include )
add_definitions ( -DMONOLITH )

set ( E_SRC openssl.c #
  verify.c asn1pars.c req.c dgst.c dh.c dhparam.c enc.c passwd.c gendh.c errstr.c 
  ca.c pkcs7.c crl2p7.c crl.c rsa.c rsautl.c dsa.c dsaparam.c ec.c ecparam.c x509.c 
  genrsa.c gendsa.c genpkey.c s_server.c s_client.c speed.c s_time.c apps.c s_cb.c 
  s_socket.c app_rand.c version.c sess_id.c ciphers.c nseq.c pkcs12.c pkcs8.c pkey.c 
  pkeyparam.c pkeyutl.c spkac.c smime.c cms.c rand.c engine.c ocsp.c prime.c ts.c )

add_executable ( openssl ${E_SRC} )
target_link_libraries ( openssl crypto ssl )

install_executable ( openssl )
install_data ( CA.sh CA.pl tsget )
# program
