# OpenWrt-gmediarender

Port [gmrender-resurrect-openhome](https://github.com/coflery/gmrender-resurrect-openhome) to OpenWrt.

## HOW TO

	cd ~
	git clone https://github.com/coflery/OpenWrt-gmediarender.git
	cd openwrt/
	./scripts/feeds update -a
	./scripts/feeds install -a
	patch -p0 < ~/OpenWrt-gmediarender/openwrt-add-gmediarender-resurrect-package.patch
	./scripts/feeds update -i
	./scripts/feeds install gmediarender
	
	make menuconfig
	// choose the right platform
	// Select gmediarender in Multimedia --> gmediarender
	// Select gstreamer1-libs in Multimedia --> gstreamer1-libs
	// Select gstreamer1-plugins-ugly in Multimedia --> gstreamer1-plugins-ugly
###Build All

	make V=s

###Build Single Package

	make package/gmediarender/compile V=s
	make package/gmediarender/install V=s
	make package/index

###Clean and Compile
	make package/gmediarender/{clean,compile} V=s

## TO DO

Test and send these patch to OpenWrt-devel. 
