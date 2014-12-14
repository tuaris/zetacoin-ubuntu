Zetacoin for Debian
===============

To build a .deb package do the following:

- Install dependencies according to https://github.com/zetacoin/zetacoin/blob/master/doc/build-unix.md
- Download the Zetacoin source tarball and extract into an empty directory.
- Rename the zetacoin source directory to zetacoin_VERSION (ie. 'zetacoin_0.9.2.4')
- Compress the directory as 'zetacoin_VERSION.orig.tar.gz'.

You should now have something like:

	|-- directory
	| |-- zetacoin_0.9.2.4
	| |-- zetacoin_0.9.2.4.orig.tar.gz

Copy the 'debian' folder from this repo into the 'zetacoin_VERSION' directory:

	|-- directory
	| |-- zetacoin_0.9.2.4
	|   `-- debian
	| |-- zetacoin_0.9.2.4.orig.tar.gz

Install dependencies **:

	apt-get install dh-make build-essential
	apt-get install devscripts fakeroot debootstrap pbuilder
	apt-get install build-essential libtool autotools-dev autoconf pkg-config libssl-dev
	apt-get install libboost-all-dev
	apt-get install libdb4.8-dev libdb4.8++-dev
	apt-get install libminiupnpc-dev
	apt-get install libqt4-dev libprotobuf-dev protobuf-compiler
	apt-get install libqrencode-dev

Enter the directory and run:

	debuild -us -uc

You will then have two packages for your platform, a Debian source package and .dsc file:

	zetacoin_0.9.2.4-1.debian.tar.gz
	zetacoin_0.9.2.4-1.dsc
	zetacoind_0.9.2.4-1_amd64.deb
	zetacoin-qt_0.9.2.4-1_amd64.deb

** For Debian 7 (Wheezy) and later:
 The oldstable repository contains db4.8 packages.
 Add the following line to /etc/apt/sources.list,
 replacing [mirror] with any official debian mirror.

	deb http://[mirror]/debian/ oldstable main