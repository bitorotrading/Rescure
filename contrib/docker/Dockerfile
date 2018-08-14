FROM debian:jessie
MAINTAINER pavik - https://github.com/pavik

ENV RECUR_VERSION=1.0.3 \
 RECUR_USER=recur

ENV RECUR_URL=https://github.com/RecurPay/RecurPay/releases/download/v$RECUR_VERSION/recur-$RECUR_VERSION-x86_64-linux-gnu.tar.gz \
 RECUR_CONF=/home/$RECUR_USER/.RecurPay/RecurPay.conf \
 RECUR_CONF_URL=https://raw.githubusercontent.com/RecurPay/RecurPay/master/RecurPay.conf

RUN apt-get -qq update && \
apt-get install -yq wget ca-certificates pwgen && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
wget $RECUR_URL -O /tmp/recur.tar.gz && \
mkdir -p /opt && \
cd /opt && \
tar xvzf /tmp/recur.tar.gz && \
rm /tmp/recur.tar.gz && \
ln -sf recur-$RECUR_VERSION recur && \
ln -sf /opt/recur/bin/recurd /usr/local/bin/recurd && \
ln -sf /opt/recur/bin/recur-cli /usr/local/bin/recur-cli && \
ln -sf /opt/recur/bin/recur-tx /usr/local/bin/recur-tx && \
adduser --uid 1000 --system ${RECUR_USER} && \
mkdir -p /home/${RECUR_USER}/.RecurPay/ && \
chown -R ${RECUR_USER} /home/${RECUR_USER} && \
echo "success: $RECUR_CONF"

USER recur
RUN wget $RECUR_CONF_URL -O $RECUR_CONF && \
    sed -i -e 's/\*your$username\*/recur/g' ${RECUR_CONF} && \
    sed -i -e 's/\*your$password\*/'`pwgen 32 1`'/g' ${RECUR_CONF} && \
    echo "Success"

EXPOSE 51572
VOLUME ["/home/recur/.RecurPay"]
WORKDIR /home/recur

ENTRYPOINT ["/usr/local/bin/recurd"]