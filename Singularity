
BootStrap: debootstrap
OSVersion: yakkety
MirrorURL: http://us.archive.ubuntu.com/ubuntu/
Include: python wget software-properties-common build-essential python-dev rsync sgml-base openssh-client xml-core

%post

	wget --no-check-certificate https://bootstrap.pypa.io/get-pip.py
	python get-pip.py
	ln -s /usr/local/bin/pip /usr/bin/pip
	pip install pymultinest ipython scipy numpy matplotlib progressbar
	add-apt-repository universe
	apt-get update
	apt-get -y install cmake git gfortran openmpi-common openmpi-bin libopenmpi-dev liblapack-dev
	git clone https://github.com/JohannesBuchner/MultiNest.git
	cd MultiNest/build/
	cmake ..
	make
	make install
	exit 0


