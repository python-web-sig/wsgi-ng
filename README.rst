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

Overall Process
===============

There are three broad phases planned (though as with all design work, it
won't be strictly dileneated). That is, folk are encouraged to experiment
with 

Phase 1 - requirements
++++++++++++++++++++++

Gathering requirements. These will come from our needs, the needs of
interop with other PEP's and of course the needs of the underlying
HTTP/1.x,HTTP/2 and Websocket protocols. I'm allowing 3 months for this to
ensure that we've had plenty of time for developers from Django, uWSGI and
so on and so forth to participate. At the end of the 3 months (mid January)
we'll stop iterating on requirements unless security or feasibility are
involved. That is, security requirements and 'this *cannot* work'
requirements can always be added. If and only if we've had broad input from
the Python web community then we may finalise things earlier.

Phase 2 - design
++++++++++++++++

Here we experiment with different ways of meeting the requirements from
Phase 1. Again, we're allowing 3 months for experimentation and design work
to take place. This needs to include proof of concept implementations that
work in mod_wsgi, uWSGI, gunicorn etc. In mid-April, we'll pick a final
design from the set of experiments that have taken place.

Phase 3 - PEP
+++++++++++++

Here we translate the final design into a PEP and enter it into the PEP
process. This will be as fast or slow as the PEP process runs.


Participating
=============

While we know things that are broken about WSGI, we probably don't know them
all, so telling us about design issues or capabilities you want to see as
issues in this respository is useful.

Specifically, please open issues at
https://github.com/python-web-sig/wsgi-ng/issues for things you want to see
in the new protocol. Whether thats 'WSGI makes me cry because X' or 'I want
to be able to write middleware that proxies to a remote server over zeromq'
- all issues are welcome.

Secondly, we need to experiment to find a good protocol that meets all our
requirements. You can add experiments as pull requests against this
repository. Experiments can be prose (e.g. a draft specification) or code
(e.g. a test implementation of a draft specification).

There is *a* draft spec based on PEP-3333 in the repository already - it is
not special or privileged - we may end up with a totally new spec rather
than that iterated one. That said please do also submit PRs to change it in
light of requirements or issues that need resolving. This repository is a
community resource where we can build consensus and working code together.

Current status
==============

We're just self assembling at the moment.

We have a `requirements document <Requirements.rst>`_.

We have a `draft PEP based on 3333 <pep-draft.rst>`_.

We may add some `experiments too <experiments.rst>`.
