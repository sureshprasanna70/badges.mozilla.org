badges.mozilla.org
==================

[![Build Status](https://travis-ci.org/mozilla/badges.mozilla.org.svg)](https://travis-ci.org/mozilla/badges.mozilla.org)
[![Requirements Status](https://requires.io/github/mozilla/badges.mozilla.org/requirements.svg)](https://requires.io/github/mozilla/badges.mozilla.org/requirements/)

[badges.mozilla.org](http://badges.mozilla.org) is a service for awarding badges to Mozillians!

Bugs and Ideas
--------------
Feel free to file them [as issues on the badges.mozilla.org project][issues]!

[issues]: https://github.com/mozilla/badges.mozilla.org/issues

Docker for development
----------------------

0. Make sure you have [docker](https://docker.io) and [fig](https://pypi.python.org/pypi/fig)
1. fig up

Development outside of Docker
-----------------------------

Here's how I get it running on my MacBook:

    git clone
    virtualenv --no-site-packages virtualenv
    . ./virtualenv/bin/activate
    pip install -r requirements/dev.txt
    # Set up a mysql database
    # Edit badgus/settings/local.py-dist and move it to local.py
    # change db credentials and add HMAC_KEYS
    ./manage.py syncdb
    ./manage.py migrate
    ./manage.py compress_assets
    ./manage.py runserver 0.0.0.0:8000

Under Ubuntu 12.10 (64 bit), all the above worked after first installing some
packages and rejiggering some files:

    sudo apt-get install build-essential python-dev python-pip \
        python-virtualenv mysql-server libmysqlclient-dev libxml2-dev \
        libxslt-dev memcached libjpeg8 libjpeg62-dev libfreetype6 \
        libfreetype6-dev

    sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so /usr/lib
    sudo ln -s /usr/lib/x86_64-linux-gnu/libfreetype.so /usr/lib
    sudo ln -s /usr/lib/x86_64-linux-gnu/libz.so /usr/lib

License
-------
This software is licensed under the [New BSD License][BSD]. For more
information, read the file ``LICENSE``.

[BSD]: http://creativecommons.org/licenses/BSD/
