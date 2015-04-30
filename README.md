# Consul docker image

[consul.io](https://consul.io/) docker image built on top of a minimal [buildroot](http://buildroot.uclibc.org/) based linux filesystem.


_based on [progrium/consul](https://github.com/progrium/docker-consul)_


### The base image

the base image `benschw/litefs` was built according the [lightweight docker containers with buildroot](https://blog.docker.com/2013/06/create-light-weight-docker-containers-buildroot/) guide. The gist of that guide is as follows:

	curl http://buildroot.uclibc.org/downloads/buildroot-2013.05.tar.bz2 | tar jx
	cd buildroot-2013.05/
	make menuconfig
	# select x86_64
	make

	cd output/images
	mkdir extra extra/etc extra/sbin extra/lib extra/lib64
	touch extra/etc/resolv.conf
	touch extra/sbin/init
	cp /lib/x86_64-linux-gnu/libpthread.so.0 /lib/x86_64-linux-gnu/libc.so.6 extra/lib
	cp /lib64/ld-linux-x86-64.so.2 extra/lib64


	cp rootfs.tar fixup.tar
	tar rvf fixup.tar -C extra .
	
	docker import - benschw/litefs < fixup.tar




