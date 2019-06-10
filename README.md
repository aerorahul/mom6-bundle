# mom6-bundle

Build bundle of base packages for a stand alone MOM6 application

--- Building the MOM6 bundle ---

    cd /somewhere/to/store/source/code
    git clone https://developer.nasa.gov/rmahajan/mom6-bundle.git

    cd /somewhere/to/build
    ecbuild /somewhere/to/store/source/code/mom6-bundle
    make -j4

The ecbuild command above will clone all the source code for the MOM6 project defined in the
CMakeLists.txt in the bundle and the make command will build them all.

To work with a different branch than the default for a given project, the branch must be
modified in the CMakeLists.txt for the bundle.

Note: ecbuild accepts all cmake flags, for example, compilers can be selected with:
    ecbuild -DCMAKE_CXX_COMPILER=/path/to/gcc-7.2/bin/g++ ${SRC}

For testing (from build directory):

    ctest

--- Working with the code ---

The CMakeLists.txt file in this directory contains the list of the repositories included
in the bundle and the branch to be used. The branch specified in the CMakeLists.txt is
the one that will be compiled. When working with your own branch, this should be changed in
the CMakeLists.txt file but it is not necessary to re-run ecbuild, make is enough.

After the fisrt build, changes in the code can be tested by re-running only
(from build directory):

    make -j4
    ctest

By default, make will not update your local repository from the remote. To update all repositories
in the bundle, run:

    make update

The update will fail for repositories that contain uncommited code. This is a safety mechanism to
avoid losing your work.
