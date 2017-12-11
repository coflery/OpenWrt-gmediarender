# OpenWrt-gmediarender

Port [gmrender-resurrect-openhome](https://github.com/coflery/gmrender-resurrect) to OpenWrt.

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
	// Choose the right platform
	// Select gmediarender in Multimedia --> gmediarender
	// Select gstreamer1-libs in Multimedia --> gstreamer1-libs
###Build All

	make V=s

###Build Single Package

	make package/gmediarender/compile V=s
	make package/gmediarender/install V=s
	make package/index

###Clean and Compile
	make package/gmediarender/{clean,compile} V=s
	
##Install to Openwrt

###Install usb SoundCard support module
	opkg install kmod-input-core
	opkg install kmod-sound-core
	opkg install kmod-usb-audio
	
#Reboot router let set enable
	reboot

#Install gstreamer's format lib
	opkg install gst1-plugins-base
	opkg install gst1-plugins-good
	opkg install gst1-plugins-ugly

#Enable gmediarender service
	/etc/init.d/gmediarender enable
	/etc/init.d/gmediarender start

## TO DO

Test and send these patch to OpenWrt-devel. 
