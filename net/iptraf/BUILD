(

  # Patch from http://koji.fedoraproject.org/koji/packageinfo?packageID=704
  patch_it $SOURCE_CACHE/$SOURCE2 1 &&

  cd src &&
  sedit  "s!/usr/local/bin!/usr/bin!"        Makefile   &&
  sedit  "s!/var/local/iptraf!/var/iptraf!"  Makefile   &&
  sedit  "s!read YESNO!YESNO == y!"          install.sh &&
  make  clean           &&
  make  PREFIX=/usr     &&
  prepare_install       &&
  make  PREFIX=/usr install         

) > $C_FIFO 2>&1
