Eclipse Mosquitto
=================

requires openssl
Build with:

LDFLAGS="-L/usr/local/ssl/ -L/usr/local/ -L/usr/local/bin/ -Wl,-rpath,/usr/local/ssl/,-rpath,/usr/local/lib/,--export-dynamic" LIBS="-ldl" CC=/c/opt/gcc-4.6.0/bin/gcc CXX=/c//opt/gcc-4.6.0/bin/g++ make WITH_DOCS=no



MAKEFILE doesn't consider LDFLAGS therefore execute command manuel when it fails with: ld cannot find -lssl (switch to src folder)

cc  -Wl -L/usr/local/ssl/ -L/usr/local/ssl/lib -L/usr/local/ -L/usr/local/bin/ -Wl,-rpath,/usr/local/ssl/,-rpath,/usr/local/lib/ mosquitto.o alias_mosq.o bridge.o conf.o conf_includedir.o context.o database.o handle_auth.o handle_connack.o handle_connect.o handle_disconnect.o handle_ping.o handle_pubackcomp.o handle_publish.o handle_pubrec.o handle_pubrel.o handle_suback.o handle_subscribe.o handle_unsuback.o handle_unsubscribe.o logging.o loop.o memory_mosq.o net.o net_mosq.o net_mosq_ocsp.o packet_datatypes.o packet_mosq.o property_broker.o property_mosq.o persist_read.o persist_read_v234.o persist_read_v5.o persist_write.o persist_write_v5.o plugin.o read_handle.o security.o security_default.o send_auth.o send_connack.o send_connect.o send_disconnect.o send_mosq.o send_publish.o send_suback.o send_subscribe.o send_unsuback.o send_unsubscribe.o service.o session_expiry.o signals.o subs.o sys_tree.o time_mosq.o tls_mosq.o utf8_mosq.o util_mosq.o util_topic.o websockets.o will_delay.o will_mosq.o -o mosquitto  -ldl -lm -lrt -lssl -lcrypto    

Continue with `make` 




Mosquitto is an open source implementation of a server for version 5.0, 3.1.1,
and 3.1 of the MQTT protocol. It also includes a C and C++ client library, and
the `mosquitto_pub` and `mosquitto_sub` utilities for publishing and
subscribing.

## Links

See the following links for more information on MQTT:

- Community page: <http://mqtt.org/>
- MQTT v3.1.1 standard: <https://docs.oasis-open.org/mqtt/mqtt/v3.1.1/mqtt-v3.1.1.html>
- MQTT v5.0 standard: <https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html>

Mosquitto project information is available at the following locations:

- Main homepage: <https://mosquitto.org/>
- Find existing bugs or submit a new bug: <https://github.com/eclipse/mosquitto/issues>
- Source code repository: <https://github.com/eclipse/mosquitto>

There is also a public test server available at <https://test.mosquitto.org/>

## Installing

See <https://mosquitto.org/download/> for details on installing binaries for
various platforms.

## Quick start

If you have installed a binary package the broker should have been started
automatically. If not, it can be started with a basic configuration:

    mosquitto

Then use `mosquitto_sub` to subscribe to a topic:

    mosquitto_sub -t 'test/topic' -v

And to publish a message:

    mosquitto_pub -t 'test/topic' -m 'hello world'

## Documentation

Documentation for the broker, clients and client library API can be found in
the man pages, which are available online at <https://mosquitto.org/man/>. There
are also pages with an introduction to the features of MQTT, the
`mosquitto_passwd` utility for dealing with username/passwords, and a
description of the configuration file options available for the broker.

Detailed client library API documentation can be found at <https://mosquitto.org/api/>

## Building from source

To build from source the recommended route for end users is to download the
archive from <https://mosquitto.org/download/>.

On Windows and Mac, use `cmake` to build. On other platforms, just run `make`
to build. For Windows, see also `readme-windows.md`.

If you are building from the git repository then the documentation will not
already be built. Use `make binary` to skip building the man pages, or install
`docbook-xsl` on Debian/Ubuntu systems.

### Build Dependencies

* c-ares (libc-ares-dev on Debian based systems) - only when compiled with `make WITH_SRV=yes`
* libwebsockets (libwebsockets-dev) - enable with `make WITH_WEBSOCKETS=yes`
* openssl (libssl-dev on Debian based systems) - disable with `make WITH_TLS=no`
* xsltproc (xsltproc and docbook-xsl on Debian based systems) - only needed when building from git sources - disable with `make WITH_DOCS=no`
* uthash / utlist - bundled versions of these headers are provided, disable their use with `make WITH_BUNDLED_DEPS=no`

Equivalent options for enabling/disabling features are available when using the CMake build.


## Credits

Mosquitto was written by Roger Light <roger@atchoo.org>

Master: [![Travis Build Status (master)](https://travis-ci.org/eclipse/mosquitto.svg?branch=master)](https://travis-ci.org/eclipse/mosquitto)
Develop: [![Travis Build Status (develop)](https://travis-ci.org/eclipse/mosquitto.svg?branch=develop)](https://travis-ci.org/eclipse/mosquitto)
Fixes: [![Travis Build Status (fixes)](https://travis-ci.org/eclipse/mosquitto.svg?branch=fixes)](https://travis-ci.org/eclipse/mosquitto)
