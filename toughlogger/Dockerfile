FROM index.alauda.cn/toughstruct/tough-pypy
MAINTAINER jamiesun <jamiesun.net@gmail.com>

VOLUME ["/var/toughlogger"]

ADD ./toughlogger.conf /etc/toughlogger.conf
ADD ./supervisord.conf /etc/supervisord.conf
ADD ./toughlogger /usr/bin/toughlogger

RUN chmod +x /usr/bin/toughlogger

RUN git clone -b master https://github.com/talkincode/toughlogger.git /opt/toughlogger

RUN ln -s /opt/toughlogger/toughctl /usr/bin/toughctl && chmod +x /usr/bin/toughctl

RUN pypy /opt/toughlogger/toughctl --initdb

EXPOSE 1820
EXPOSE 1514
EXPOSE 514/udp

ENTRYPOINT ["/usr/bin/toughlogger","start"]

