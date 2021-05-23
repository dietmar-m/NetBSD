DESTDIR=
GAMESDIR=/usr/games
INSTALL=/usr/bin/install
USER=joshua

all:
install:
	$(INSTALL) -d $(DESTDIR)$(GAMESDIR)
	$(INSTALL) -m 755 -o root -g games wopr $(DESTDIR)$(GAMESDIR)
	grep ^telnet $(DESTDIR)/etc/gettytab ||\
		echo 'telnet:im=WOPR\r\n:lm=logon\c:' >>\
			$(DESTDIR)/etc/gettytab
	if useradd -m -g games $(USER); then\
		passwd $(USER);\
		echo 'echo $TERM | grep xterm > /dev/null && TERM=xterm'\
			>> $(DESTDIR)/home/$(USER)/.profile;\
		echo 'exec $(GAMESDIR)/wopr'\
			>> $(DESTDIR)/home/$(USER)/.profile;\
	fi

