# synology-crowdsec-firewall-bouncer-spk
#
# SPDX-License-Identifier: MIT
#
# Copyright (C) 2021-2022 Gerald Kerma <gandalf@gk2.net>
# Copyright (C) 2021-2022 CrowdSec <crowdsec@crowdsec.net>
#

SPK_NAME = crowdsec-firewall-bouncer
SPK_VERS = 0.0.34
SPK_REV = 1
SPK_ICON = src/$(SPK_NAME).png

DISPLAY_NAME = CrowdSec-Firewall-Bouncer
DESCRIPTION = Crowdsec-Firewall-Bouncer will fetch new and old decisions from a CrowdSec API to add them in a blocklist used by supported firewalls.
CHANGELOG = "0.0.34-1: Update to cs-firewall-bouncer 0.0.34, use system ipset via opkg"

SUPPORTED_ARCHS = x64-7.1 aarch64-7.1 armv7-7.1

THIRDPARTY = "yes"
HOMEPAGE = "https://www.crowdsec.net"
LICENSE = "MIT"

DISTRIBUTOR = "CrowdSec"
DISTRIBUTOR_URL = "https://www.crowdsec.net"

MAINTAINER = "CyberMind"
MAINTAINER_URL = "https://cybermind.fr"

RELOAD_UI = yes
STARTABLE = yes

DEPENDS  = cross/$(SPK_NAME)
##DEPENDS += cross/ipset
##DEPENDS += cross/ipset-kernel

##SPK_DEPENDS = "crowdsec"
OPTIONAL_DEPENDS = "crowdsec"

include ../../mk/spksrc.common.mk

ifeq ($(call version_ge, ${TCVERSION}, 7.0),1)
	CONF_DIR = src/conf_7
	SPK_GROUP = sc-crowdsec
	SPK_USER = crowdsec
	SYSTEM_GROUP = system
	SERVICE_USER = auto
else ifeq ($(call version_ge, ${TCVERSION}, 6.0),1)
	CONF_DIR = src/conf_6
	SPK_GROUP = sc-crowdsec
	SPK_USER = crowdsec
	SYSTEM_GROUP = system
	SERVICE_USER = root
endif

SERVICE_SETUP = src/service-setup.sh

PRE_STRIP_TARGET	= nop
STRIP_TARGET		= nop
POST_STRIP_TARGET	= nop

SPK_USR_LOCAL_LINKS  = bin:usr/sbin/crowdsec-firewall-bouncer

SPK_COMMANDS  = usr/sbin/crowdsec-firewall-bouncer

include ../../mk/spksrc.spk.mk
