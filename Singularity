Bootstrap:docker  
From:fedora:latest  

%labels
MAINTAINER baber@iastate.edu

%environment
SPACK_ROOT=/opt/spack
export SPACK_ROOT
export PATH=$SPACK_ROOT/bin:$PATH
#export TMPDIR=/tmp

%runscript
spack find 

%post  
export SPACK_ROOT=/opt/spack
#export TMPDIR=/tmp
#kept running out of space on my host /tmp
#even though I had changed SINGULARITY_CACHEDIR, set singularity.conf not to mount tmp
#even tried hacking on the defaults.py in libexec
#broke up the dnf installs into chunks, seems to clean up after itself in phases and fits in my small tmp
#don't think the dnf clean is actually doing anything
dnf clean all
dnf -y install git python3 
dnf clean packages
dnf -y install gcc gcc-c++ curl 
dnf clean packages
dnf -y install gnupg2 sed patch 
dnf clean packages
dnf -y install file unzip gzip
dnf clean packages
ln -f -s /usr/bin/python3 /usr/bin/python
#git clone https://github.com/spack/spack.git $SPACK_ROOT
git clone https://github.com/researchit/spack.git $SPACK_ROOT
#cp $SPACK_ROOT/etc/spack/defaults/config.yaml $SPACK_ROOT/etc/spack

#export SPACK_CONF_FILE=$SPACK_ROOT/etc/spack/config.yaml

#sed -i -e 's|install_tree: $spack/opt/spack|install_tree: ~/spack_packages/|g' $SPACK_CONF_FILE
#sed -i -e 's|source_cache: $spack/var/spack/cache|source_cache: $tempdir/var/spack/cache|g' $SPACK_CONF_FILE
#sed -i '/- \/nfs\/tmp2\/$user/d' $SPACK_CONF_FILE
#sed -i '/- $spack\/var\/spack\/stage/d' $SPACK_CONF_FILE
#sed -i -e 's|$spack/share/spack|\~/spack_modules/share/spack|g' $SPACK_CONF_FILE
#chmod -R 777 /opt/spack
