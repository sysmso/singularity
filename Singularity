
BootStrap: debootstrap
OSVersion: yakkety
MirrorURL: http://us.archive.ubuntu.com/ubuntu/
Include: python wget software-properties-common build-essential python-dev rsync sgml-base openssh-client xml-core

%setup

    cp pymultinest_demo_minimal.py $SINGULARITY_ROOTFS

%post

	wget --no-check-certificate https://bootstrap.pypa.io/get-pip.py
	python get-pip.py
	ln -s /usr/local/bin/pip /usr/bin/pip
	pip install pymultinest ipython scipy numpy matplotlib progressbar
	add-apt-repository universe
	apt-get update
	apt-get -y install cmake git gfortran openmpi-common openmpi-bin libopenmpi-dev liblapack-dev
	cd /tmp
    git clone https://github.com/JohannesBuchner/MultiNest.git
	cd MultiNest/build/
	cmake ..
	make
	make install
    echo "export LD_LIBRARY_PATH=/usr/local/lib/" > /environment
    apt-get clean
    mkdir /scratch
    chmod -R 777 /scratch
    mv /pymultinest_demo_minimal.py /scratch
	exit 0

%runscript
	echo "Arguments received: $*"
	exec /usr/bin/python "$@"
