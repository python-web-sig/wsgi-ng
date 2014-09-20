This repository is for drafting a revision to the WSGI spec.

Who
===

Right now we're figuring out who has the time to contribute to this
on the web-sig list, the We below refers to whomever ends up being
involved :)

We want to create a clean common API for applications and middleware
written in a post HTTP/2 world - where single servers may accept up to
all three of HTTP/1.x, HTTP/2 and Websocket connections, and
applications and middleware want to be able to take advantage of
HTTP/2 and websockets when available, but also degrade gracefully. We
also want to ensure that there is a graceful incremental path to
adoption of the new API, including Python 2.7 support, and shims to
enable existing WSGI apps/middleware/servers to respectively be
contained, contain-or-be-contained and contain, things written to this
new API. We want a clean, fast and approachable API, and we want to
ensure that its no less friendly to work with than WSGI, for all that
it will expose much more functionality.

Governance
==========

We plan to produce a PEP and reference code. That will be done by direct
collaboration from folk with time and energy. We're not interested in
debating everything to death until we have working code showing that
we've got *something* feasible. At that point we'll move into the regular
PEP process on python-ideas@python.org. This incrementally more public
approach is intended to mitigate against burnout that has negatively
affected previous WSGI overhaul approaches.

Participating
=============

While we know things that are broken about WSGI, we probably don't know them
all, so telling us about design issues or capabilities you want to see as
issues in this respository is useful.

Courteous feedback on the draft PEP as it comes together is welcomed at any
point :). Pull requests that update it to fix issues etc are even better.

Writing code to implement / extend the draft we come up with is even better
of course!

Current status
==============

We're just self assembling at the moment.
