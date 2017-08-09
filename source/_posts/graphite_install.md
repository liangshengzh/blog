title: graphite 安装
date: 2017-08-06 20:02:30
tags: graphite
---


1. graphite 安装

更新依赖
yum install python-devel cairo-devel libffi-devel

安装pip
wget https://bootstrap.pypa.io/get-pip.py
python get-pip.py


pip install https://github.com/graphite-project/carbon/tarball/1.0.2 --install-option="--prefix=/data/graphite" --install-option="--install-lib=/data/graphite/lib"
pip install https://github.com/graphite-project/graphite-web/tarball/1.0.2 --install-option="--prefix=/data/graphite" --install-option="--install-lib=/data/graphite/webapp"

pushd /data/graphite/conf
cp carbon.conf.example carbon.conf
cp storage-schemas.conf.example storage-schemas.conf

 PYTHONPATH=/data/graphite/webapp  /usr/bin/django-admin.py migrate --settings=graphite.settings

pip install https://github.com/graphite-project/ceres/tarball/master


yum install libffi-deve

pip install graphite-api --install-option="--prefix=/data/graphite"

# cd /opt/graphite/conf
# cp aggregation-rules.conf.example aggregation-rules.conf
# cp blacklist.conf.example blacklist.conf
# cp carbon.conf.example carbon.conf
# cp carbon.amqp.conf.example carbon.amqp.conf
# cp relay-rules.conf.example relay-rules.conf
# cp rewrite-rules.conf.example rewrite-rules.conf
# cp storage-schemas.conf.example storage-schemas.conf
# cp storage-aggregation.conf.example storage-aggregation.conf
# cp whitelist.conf.example whitelist.conf
# vi carbon.conf


源码安装.
pip install -r requirements.txt
python setup.py  install --prefix=/data/graphite --install-lib=/data/graphite/lib
pip install -r requirements.txt
python setup.py  install --prefix=/data/graphite --install-lib=/data/graphite/webapp
python setup.py install
pip install -r requirements.txt
cp carbon.conf.example carbon.conf
cp storage-schemas.conf.example storage-schemas.conf



yum install -y uwsgi-plugin-python uwsgi

uwsgi --chdir /data/graphite/conf/ --wsgi-file graphite.wsgi --socket 127.0.0.1:43210

uwsgi="/opt/graphite/bin/uwsgi"
prog=$(basename "$uwsgi")
UWSGI_CONF_DIR="/etc/uwsgi"
UWSGI_LOG_DIR="/var/log/uwsgi"
PIDFILE_DIR="/var/run/uwsgi"



https://pip.pypa.io/en/stable/installing/
http://graphite.readthedocs.io/en/latest/install-pip.html



git clone https://github.com/graphite-project/graphite-web.git && cd graphite-web && git checkout tags/1.0.2
git clone https://github.com/graphite-project/carbon.git && cd carbon && git checkout tags/1.0.2 && cd ..
git clone https://github.com/graphite-project/whisper.git && cd whisper && git checkout tags/1.0.2 && cd ..


PYTHONPATH=/data/graphite/webapp /usr/lib/python2.7/site-packages/django/bin/django-admin.py syncdb --settings=graphite.settings
