# Only build psutils
OPTS+=" --disable-all-pkgs --enable-psutils --enable-ipc --enable-shared --enable-static=no --disable-multiplatform --disable-native-texlive-build --with-gs=gs"  &&

if ! module_installed libX11 ; then
  # Prevents risk of circular dependency: groff -> man -> libX11
  OPTS+=" --without-x"
fi  &&

mkdir tex-build &&
cd tex-build    &&
../configure --prefix=/usr $OPTS &&
default_make
