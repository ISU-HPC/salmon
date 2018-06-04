bootstrap: docker
FROM: ubuntu:18.04

%labels

AUTHOR Yasasvy Nanyam ynanyam@iastate.edu

%post

apt update
apt install -y git gcc make g++ cmake libboost-all-dev liblzma-dev libbz2-dev \
                ca-certificates zlib1g-dev curl unzip autoconf

# install salmon

cd /
export SALMON_VERSION=0.10.1
curl -k -L https://github.com/COMBINE-lab/salmon/archive/v${SALMON_VERSION}.tar.gz -o salmon-v${SALMON_VERSION}.tar.gz
tar xzf salmon-v${SALMON_VERSION}.tar.gz
cd salmon-${SALMON_VERSION}
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local
make
make install


cd /
rm -rf salmon-v${SALMON_VERSION}.tar.gz

# Add PATH

echo 'export PATH=/usr/local/bin:$PATH' >>$SINGULARITY_ENVIRONMENT
echo 'export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH' >>$SINGULARITY_ENVIRONMENT
