FROM index.alauda.cn/toughstruct/tough-pypy
MAINTAINER jamiesun <jamiesun.net@gmail.com>

VOLUME ["/var/toughlogger"]

ADD ./toughlogger.conf /etc/toughlogger.conf
ADD ./supervisord.conf /etc/supervisord.conf
ADD ./toughlogger /usr/bin/toughlogger

RUN chmod +x /usr/bin/toughlogger

RUN git clone -b master https://github.com/talkincode/toughlogger.git /opt/toughlogger

RUN ln -s /opt/toughlogger/toughctl /usr/bin/toughctl && chmod +x /usr/bin/toughctl

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

RUN pypy /opt/toughlogger/toughctl --initdb

RUN echo "set nocompatible" >> /root/.vimrc && echo "set backspace=2" >> /root/.vimrc

EXPOSE 1820
EXPOSE 1514
EXPOSE 514/udp

ENTRYPOINT ["/usr/bin/toughlogger","start"]

