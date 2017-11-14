Bootstrap:docker  
From:fedora:latest  

%labels
MAINTAINER baber@iastate.edu

%environment
SPACK_ROOT=/opt/spack
export SPACK_ROOT
export PATH=$SPACK_ROOT/bin:$PATH

%runscript
spack find 

%post  
export SPACK_ROOT=/opt/spack
dnf -y install git python3 gcc curl gnupg2 sed
ln -f -s /usr/bin/python3 /usr/bin/python
if [ -d "/opt/spack" ]; then
  cd $SPACK_ROOT && git pull
else
  git clone https://github.com/spack/spack.git $SPACK_ROOT
fi
cp $SPACK_ROOT/etc/spack/defaults/config.yaml $SPACK_ROOT/etc/spack
sed -i -e 's|install_tree: $spack/opt/spack|install_tree: $tmpdir/spack/|g' $SPACK_ROOT/etc/spack/defaults/config.yaml
chmod -R 777 /opt/spack
