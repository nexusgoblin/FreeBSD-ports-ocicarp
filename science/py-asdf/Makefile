PORTNAME=	asdf
PORTVERSION=	3.2.0
CATEGORIES=	science python
MASTER_SITES=	PYPI
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Python tools to handle ASDF files
WWW=		https://asdf.readthedocs.io/en/latest/ \
		https://github.com/asdf-format/asdf

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}setuptools>=60:devel/py-setuptools@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}setuptools-scm>=3.4:devel/py-setuptools-scm@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}wheel>=0:devel/py-wheel@${PY_FLAVOR}
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}asdf-standard>=1.1.0:science/py-asdf-standard@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}asdf-transform-schemas>=0.3:science/py-asdf-transform-schemas@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}attrs>=20.1.0:devel/py-attrs@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}importlib-metadata>=4.11.4:devel/py-importlib-metadata@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}jmespath>=0.6.2:devel/py-jmespath@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}numpy>=1.22,1:math/py-numpy@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}packaging>=19:devel/py-packaging@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}yaml>=5.4.1:devel/py-yaml@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}semantic-version>=2.8:devel/py-semantic-version@${PY_FLAVOR}

USES=		python:3.9+ shebangfix
USE_PYTHON=	autoplist concurrent pep517

NO_ARCH=	yes

SHEBANG_FILES=	asdf/_jsonschema/json/bin/jsonschema_suite

OPTIONS_DEFINE=	ALL
OPTIONS_DEFAULT=ALL
ALL_DESC=	Lz4 compression algorithm support

ALL_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}lz4>=0.10:archivers/py-lz4@${PY_FLAVOR}

.include <bsd.port.mk>
