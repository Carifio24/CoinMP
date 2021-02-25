# Copyright (C) 2006 International Business Machines.
# All Rights Reserved.
# This file is distributed under the Common Public License.

## $Id: configure.ac 71 2006-07-14 17:44:04Z jpfasano $

# Author:  Andreas Waechter            IBM    2006-04-13

AC_INIT([CoinMP],[devel],[https://github.com/coin-or/CoinMP/issues/new],[coin-or-coinmp],[https://github.com/coin-or/CoinMP])

AC_COPYRIGHT([
Copyright 2006 International Business Machines and others.
All Rights Reserved.
This file is part of the open source package CoinMP which is distributed
under the Common Public License.])

# List one file in the package so that the configure script can test
# whether the package is actually there.
AC_CONFIG_SRCDIR(src/CoinMP.h)

# Do some initialization work (version numbers, change prefix default, ...)
AC_COIN_INITIALIZE

#############################################################################
#                         Standard build tool stuff                         #
#############################################################################

# Get the name of the C++ compiler and appropriate compiler options
AC_COIN_PROG_CXX

# Initialize libtool
AC_COIN_PROG_LIBTOOL

# set RPATH_FLAGS to the compiler link flags required to hardcode location
# of the shared objects (expanded_libdir is set somewhere in configure before)
# (use in examples Makefile)
AC_COIN_RPATH_FLAGS([$expanded_libdir])

#############################################################################
#                            COIN-OR components                             #
#############################################################################

# Required packages.
# We need Clp, Cbc, and the OSI interface to CLP to build CoinCbc.cpp.

AC_COIN_CHK_PKG(Cbc, [CoinMPLib])
AC_COIN_CHK_PKG(Clp, [CoinMPLib])
if test $coin_has_cbc != yes; then
    AC_MSG_ERROR([Required package Cbc not available.])
fi
if test $coin_has_clp != yes; then
    AC_MSG_ERROR([Required package Clp not available.])
fi

##############################################################################
#                   Finishing up by writing all the output                   #
##############################################################################

# Here list all the files that configure should create (except for the
# configuration header file)
AC_CONFIG_FILES([Makefile
                 src/Makefile
                 test/Makefile
                 examples/Makefile
                 coinmp.pc
                 coinmp-uninstalled.pc])


# Here put the location and name of the configuration header file
AC_CONFIG_HEADER([src/config.h src/config_coinmp.h])

AC_COIN_FINALIZE_FLAGS(CoinMPLib)

# Finally, we let configure write all the output...
AC_COIN_FINALIZE