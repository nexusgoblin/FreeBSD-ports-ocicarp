PORTNAME=	dwave-cloud-client
DISTVERSION=	0.11.3
CATEGORIES=	science python www # quantum-computing
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	DWave: REST interface to communicate with D-Wave Solver API servers
WWW=		https://github.com/dwavesystems/dwave-cloud-client

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

PY_DEPENDS=	${PYTHON_PKGNAMEPREFIX}authlib>=1.2:security/py-authlib@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}click>=7:devel/py-click@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}dateutil>=2.7:devel/py-dateutil@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}diskcache>=5.2.1:devel/py-diskcache@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}dwave-networkx>=0.8.9:science/py-dwave-networkx@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}homebase>=1.0:devel/py-homebase@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}importlib-metadata>=5.0.0:devel/py-importlib-metadata@${PY_FLAVOR} \
		${PYNUMPY} \
		${PYTHON_PKGNAMEPREFIX}packaging>=19:devel/py-packaging@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}plucky>=0.4.3:devel/py-plucky@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}pydantic2>=2:devel/py-pydantic2@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}requests>=2.18:www/py-requests@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}typing-extensions>=4.5.0:devel/py-typing-extensions@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}werkzeug>=2.2:www/py-werkzeug@${PY_FLAVOR}
BUILD_DEPENDS=	${PY_DEPENDS}
RUN_DEPENDS=	${PY_DEPENDS}
TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}coverage>0:devel/py-coverage@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}dwave-networkx>=0.8.9:science/py-dwave-networkx@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}mock>0:devel/py-mock@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}parameterized>0:devel/py-parameterized@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}requests-mock>0:www/py-requests-mock@${PY_FLAVOR}

USES=		python
USE_PYTHON=	distutils cython autoplist unittest # 1 test fail, probably due to devel/py-homebase issues, also https://github.com/dwavesystems/dwave-cloud-client/issues/533

USE_GITHUB=	yes
GH_ACCOUNT=	dwavesystems

NO_ARCH=	yes

TEST_ENV=	${MAKE_ENV} PYTHONPATH=${STAGEDIR}${PYTHONPREFIX_SITELIBDIR}

.include <bsd.port.mk>
