(

  #It seems like someone missed -lz here...
  sedit "s:\(librsyslog_la_LIBADD = \$(DL_LIBS) \$(RT_LIBS)\):\1 \$(ZLIB_LIBS):" runtime/Makefile.in

  OPTS+=" --enable-regexp      \
          --enable-largefile   \
          --enable-klog        \
          --enable-inet        \
          --enable-imfile      \
          --enable-mail        \
          --enable-fsstnd      \
          --enable-rsyslogd    \
          --enable-rsyslogrt   \
          --enable-rsyslogd    \
          --disable-rfc3195    \
          --enable-cached-man-pages"  &&

  default_build  &&

  if [ ! -f /etc/rsyslog.conf ]; then
     install -m 644 $SCRIPT_DIRECTORY/rsyslog.conf /etc/rsyslog.conf
  fi &&
  if [ ! -d /etc/rsyslog.d/20-default.conf ]; then
    install -Dm0644 $SCRIPT_DIRECTORY/20-default.conf /etc/rsyslog.d/20-default.conf
  fi &&
  mkdir -p /usr/share/doc/rsyslog/scripts/{mysql,pqsql} &&
  install -m 644 plugins/ommysql/createDB.sql /usr/share/doc/rsyslog/scripts/mysql/ &&
  install -m 644 plugins/ompgsql/createDB.sql /usr/share/doc/rsyslog/scripts/pqsql/ &&

  gather_docs doc/rsyslog-example.conf

) > $C_FIFO 2>&1
