# $OpenBSD: Makefile,v 1.3 2019/01/09 04:27:09 bentley Exp $

COMMENT =	framework for Verilog RTL synthesis

GH_ACCOUNT =	YosysHQ
GH_PROJECT =	yosys
GH_TAGNAME =	yosys-0.8
DISTNAME =	${GH_TAGNAME}

CATEGORIES =	cad

HOMEPAGE =	http://www.clifford.at/yosys/
MAINTAINER =	Alessandro De Laurenzis <just22@atlantide.t28.net>

# ISC (yosys), MIT (MiniSat)
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB +=	${COMPILER_LIBCXX} ${MODTCL_WANTLIB} c m readline ffi

# C++11
COMPILER =	base-clang ports-gcc

MODULES =	lang/python \
		lang/tcl
MODPY_VERSION =	${MODPY_DEFAULT_VERSION_3}
CONFIGURE_STYLE = none

BUILD_DEPENDS =	devel/bison \
		shells/bash

RUN_DEPENDS =	cad/abc \
		math/graphviz \
		shells/bash

LIB_DEPENDS =	${MODTCL_LIB_DEPENDS} \
		devel/libffi

TEST_DEPENDS =	cad/abc \
		lang/gawk \
		lang/iverilog \
		shells/bash

USE_GMAKE =	Yes

MAKE_FLAGS =	CXX="${CXX}" \
		LD="${CXX} -L${LOCALBASE}/lib" \
		PRETTY=0

# ports-gcc 4.9 requires explicit -std=c++11
MAKE_ENV =	ABCEXTERNAL=${LOCALBASE}/bin/abc \
		CXXFLAGS="${CXXFLAGS} -std=c++11" \
		TCL_VERSION="${MODTCL_LIB}" \
		TCL_INCLUDE="${MODTCL_INCDIR}"

TEST_ENV =	MAKE="${MAKE_PROGRAM}"

FAKE_FLAGS =	PREFIX="${TRUEPREFIX}"

do-configure:
	@${SUBST_CMD} ${WRKSRC}/kernel/yosys.cc
	@cd ${WRKBUILD} && exec ${MAKE_PROGRAM} config-gcc

post-install:
	${MODPY_BIN} ${MODPY_LIBDIR}/compileall.py \
	    ${PREFIX}/share/yosys/python3

.include <bsd.port.mk>
