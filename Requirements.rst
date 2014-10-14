Overview
========

These are the functional requirements for any successful design. Where the
requirements are too high level to be actionable, please help us refine them :).

Requirements
============

#. Support servers speaking HTTP/1.x, HTTP/2 and Websockets (potentially all on
   a single port).
#. Support graceful degradation for applications that can use HTTP/2 but still
   support HTTP/1.x requests.
#. Graceful incremental adoption path - no upgrade-all-components requirement
   baked into the design.
#. Support Python 2.7 and 3.x (where x is not yet discussed)
#. Support the existing ecosystem of containers (such as mod_wsgi)
   new API. We want a clean, fast and approachable API, and we want to
   ensure that its no less friendly to work with than WSGI, for all that
   it will expose much more functionality.
#. Apps need to be able to tell what protocol is in use, and what optional
   features are available. For instance, HTTP/2 PUSH PROMISE is an optional
   feature that can be disabled by clients. Websockets needs to expose a socket
   like object, and so on.
#. Support websockets
#. Support HTTP/2
#. Support HTTP/1.x [ which may be just 'point at PEP-3333'. ]
#. Continue to support lightweight shims being built on top such as
   https://github.com/Pylons/webob/blob/master/webob/request.py

Corollaries
===========

#. May well want to use `python futures <http://python-futures.org>`_ to get
   bytes on Python 2.7.
#. Will need old to new and new to old shims to enale upgrading one layer in
   a middleware stack at a time.
#. Cannot be coarsely incompatible with WSGI, or writing shims will be very
   fragile.
#. Cannot hand the connection socket to apps (pending confirmation from
   container authors).

Not requirements
================

These are things that we've discussed but haven't [yet] decided to make into
requirements for the design, or which we have decided definitely are not
requirements.

Implementing new protocols as middleware
++++++++++++++++++++++++++++++++++++++++

gunicorn exposes the socket that requests were received on, allowing apps to
write anything they want - e.g. taking over the socket, which is how websockets
can be implemented there. gevent uses a custom handler_class to inject websocket
data into the environment. Neither approach is standardised (such that all
containers support it). Making new protocol implementations be something that
can routinely be done without revving WSGI would be nice, but its not clear that
its compatible with the requirement for supporting e.g. mod_wsgi. Input from
container maintainers is needed!
