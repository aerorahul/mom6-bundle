################################################################################
# MOM6-BUNDLE
################################################################################

project( mom6-bundle C Fortran )

cmake_minimum_required( VERSION 3.3.2 FATAL_ERROR )

include( ecbuild_bundle )

set( ECBUILD_DEFAULT_BUILD_TYPE Release )
set( ENABLE_MPI ON CACHE BOOL "Compile with MPI" )

ecbuild_bundle_initialize()

ecbuild_requires_macro_version( 2.7 )

ecbuild_bundle( PROJECT gsw GIT "https://github.com/JCSDA/GSW-Fortran.git" BRANCH develop UPDATE )
ecbuild_bundle( PROJECT fms GIT "https://github.com/JCSDA/FMS.git" BRANCH dev/master-ecbuild UPDATE )
ecbuild_bundle( PROJECT cvmix GIT "https://github.com/JCSDA/CVMix-src.git" BRANCH feature/ecbuild UPDATE )
ecbuild_bundle( PROJECT geokdtree GIT "https://github.com/JCSDA/geoKdTree.git" BRANCH feature/ecbuild UPDATE )
ecbuild_bundle( PROJECT mom6_da_hooks GIT "https://github.com/JCSDA/MOM6_DA_hooks.git" BRANCH feature/ecbuild UPDATE )
ecbuild_bundle( PROJECT mom6 GIT "https://github.com/JCSDA/MOM6.git" BRANCH dev/master-ecbuild UPDATE )

ecbuild_bundle_finalize()
