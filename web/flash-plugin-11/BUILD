(

  prepare_install &&
  install -Dm755 libflashplayer.so /usr/lib/lunar/plugins/libflashplayer.so &&
  install -m755 usr/bin/flash-player-properties /usr/bin &&
  install -Dm755 usr/share/pixmaps/flash-player-properties.png /usr/share/pixmaps/flash-player-properties.png &&
  install -m755 usr/share/applications/flash-player-properties.desktop /usr/share/applications/ &&
  cp -af usr/share/icons /usr/share/ &&

  if module_installed kdelibs ; then
    cp -af usr/share/kde4/services/* /usr/share/kde4/services/ &&
    if [ `arch` == "x86_64" ] ; then
      cp -af usr/lib64/kde4/* /usr/lib/kde4/
    else
      cp -af usr/lib/* /usr/lib/
    fi
  fi &&

  # Enable 3D acceleration using OpenGL
  if ! grep -q OverrideGPUValidation /etc/adobe/mms.cfg 2>/dev/null ; then
    # From http://www.nvnews.net/vbulletin/showthread.php?t=148409&page=7
    mkdir -p /etc/adobe/ &&
    echo "OverrideGPUValidation=true" >> /etc/adobe/mms.cfg
  fi &&

  if in_depends $MODULE libvdpau ; then
    if ! grep -q EnableLinuxHWVideoDecode /etc/adobe/mms.cfg 2>/dev/null ; then
      # From http://www.nvnews.net/vbulletin/showthread.php?t=148409&page=5
      mkdir -p /etc/adobe/ &&
      echo "EnableLinuxHWVideoDecode=1" >> /etc/adobe/mms.cfg
    fi
  fi &&

# This appears to have fixed the constant crashing of flash since the version bump
# From http://macromedia.mplug.org/
  if ! grep -q WindowlessDisable=true /etc/adobe/mms.cfg 2>/dev/null ; then
    echo "WindowlessDisable=true" >> /etc/adobe/mms.cfg
  fi

) > $C_FIFO 2>&1
