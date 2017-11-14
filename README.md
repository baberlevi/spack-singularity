# work in progress

attempt to build a base singularity image with spack that can be used as the bootstrap for
other singularity images that would perform the spack install of a particular package

currently having an issue with stage directory for spack attempting to write to 
the immutable squashfs 

as expected, the child container will happily install during %post since it can write

