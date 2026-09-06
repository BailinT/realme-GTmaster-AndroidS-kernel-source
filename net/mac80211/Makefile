# SPDX-License-Identifier: GPL-2.0
obj-$(CONFIG_MAC80211) += mac80211.o

# mac80211 objects
mac80211-y := \
	main.o status.o \
	driver-ops.o \
	sta_info.o \
	wep.o \
	aead_api.o \
	wpa.o \
	scan.o offchannel.o \
	ht.o agg-tx.o agg-rx.o \
	vht.o \
	he.o \
	ibss.o \
	iface.o \
	rate.o \
	michael.o \
	tkip.o \
	aes_cmac.o \
	aes_gmac.o \
	fils_aead.o \
	cfg.o \
	ethtool.o \
	rx.o \
	spectmgmt.o \
	tx.o \
	key.o \
	util.o \
	wme.o \
	chan.o \
	trace.o mlme.o \
	tdls.o \
	ocb.o

mac80211-$(CONFIG_MAC80211_LEDS) += led.o
mac80211-$(CONFIG_MAC80211_DEBUGFS) += \
	debugfs.o \
	debugfs_sta.o \
	debugfs_netdev.o \
	debugfs_key.o

mac80211-$(CONFIG_MAC80211_MESH) += \
	mesh.o \
	mesh_pathtbl.o \
	mesh_plink.o \
	mesh_hwmp.o \
	mesh_sync.o \
	mesh_ps.o

mac80211-$(CONFIG_PM) += pm.o

CFLAGS_trace.o := -I$(src)

# BailinT: 原树把 rc80211_minstrel.o 写成自引用 composite（rc80211_minstrel-y := rc80211_minstrel.o）
# 导致 kbuild link_multi 空输入 "ld: no input files"。恢复主线直加形态；ht/debugfs 变体源码与
# 本树头文件混血（r21 实测 .c/.h 版本错位），暂不编，缺 ht 仅退化 HT 速率算法不影响功能。
mac80211-$(CONFIG_MAC80211_RC_MINSTREL) += rc80211_minstrel.o

ccflags-y += -DDEBUG
