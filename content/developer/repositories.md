---
title: Understanding ejabberd and its dependencies | ejabberd documentation
---

# Understanding ejabberd and its dependencies

We wanted to make sure that ejabberd is modular and that parts that
can be of interest for other Erlang projects can be reused.

Not only we are massive open source contributors to Erlang community
and ecosystem, but we are also trying to help even more by reviewing
your pull requests. Do not hesitate to submit some on any of the many
repositories mentioned here.

## ejabberd dependencies

### Required dependencies

The main ejabberd repository is
[processone/ejabberd](https://github.com/processone/ejabberd)

There is a couple of thousands of forks, but we actively maintain
ejabberd to make it the most reliable and up to date version. This is
thus your best starting point.

When you build ejabberd yourself, the build chain will download a few
Erlang dependencies:

* [processone/cache_tab](https://github.com/processone/cache_tab):
  Flexible in-memory Erlang caching module.
* [processone/eiconv](https://github.com/processone/eiconv): Native
  iconv driver for Erlang. This is use for fast character encoding
  conversion.
* [processone/xml](https://github.com/processone/xml): Fast native
  Expat based Erlang XML parsing library. XML is the core of XMPP so
  we needed to provide the fast and more robust XML parsing stack as
  possible. It means that if you are looking for a great XML parser,
  reusing p1_xml is probably a great idea.
* [processone/stringprep](https://github.com/processone/stringprep):
  Fast and efficient Erlang Stringprep native driver. Stringprep is
  heavily used in XMPP to define encoding rules of various XMPP
  objects.
* [processone/p1_yaml](https://github.com/processone/p1_yaml): Native
  Erlang interface to libyaml, for fast robust YAML parsing. This is
  needed by our new config file format.
* [processone/zlib](https://github.com/processone/zlib): Native zlib
  driver for Erlang. Used for fast / efficient stream compression.
* [processone/tls](https://github.com/processone/tls): Erlang native
  driver for TLS / SSL. It is build for performance and is more
  scalable that Erlang SSL driver. If your Erlang server is handling
  heavy load and is using TLS, we strongly recommand you check /
  compare with this driver.
* [processone/p1_sip](https://github.com/processone/p1_sip):
  ProcessOne SIP protocol support to add SIP-based voice capabilities
  to ejabberd.
* [processone/stun](https://github.com/processone/stun):
  Implementation of
  [Session Traversal Utilities for NAT](http://en.wikipedia.org/wiki/STUN). It
  is used for XMPP and SIP media capabilities, to help client discover
  their visible IP address and allow them to get in touch through
  NAT. This is basically useful for voice and file transfers.
* [processone/p1_utils](processone/p1_utils): This is extra Erlang
  modules developed for ejabberd but that can be useful in other
  Erlang applications.
* [processone/p1_logger](https://github.com/processone/p1_logger):
  Logger wrapper to allow selecting your prefered logger at build
  time.
* [basho/lager](https://github.com/basho/lager): Erlang logger module.
* [DeadZen/goldrush](https://github.com/DeadZen/goldrush): Small
  Erlang app that provides fast event stream processing. It is used by
  lager.
* [vaxelfel/eHyperLogLog](https://github.com/vaxelfel/eHyperLogLog):
  HyperLogLog, a distinct values estimator, in Erlang. Used for
  analytics.

### Optional dependencies

Then, we use a few other dependant repositories that may be used if you
have enable support in the configure script.

Here are the dependancies for relational database support:

* [processone/mysql](https://github.com/processone/mysql): Pure Erlang
  MySQL driver.
* [processone/pgsql](https://github.com/processone/pgsql): Pure Erlang
  PostgreSQL driver

Here are the dependencies for Elixir support:

* [elixir-lang/elixir](https://github.com/elixir-lang/elixir): Used to
  write ejabberd modules in Elixir programming language.
* [yrashk/rebar_elixir_plugin](https://github.com/yrashk/rebar_elixir_plugin):
  Plugin for rebar build tool to support Elixir modules compilation.

Here are the dependencies for Riak support:

* [basho/riak-erlang-client](https://github.com/basho/riak-erlang-client):
  Erlang client for Riak database.
* [basho/riak_pb](https://github.com/basho/riak_pb): Riak Protocol
  Buffer Messages. Used by both Riak client and Riak server.
* [basho/erlang_protobuffs](https://github.com/basho/erlang_protobuffs):
  An implementation of Google's Protocol Buffers for Erlang. This is
  the low level protocol used by Riak database.
* [eproxus/meck](https://github.com/eproxus/meck): Mock library used
  to write Erlang protobuffs test suite.

After you have build ejabberd from source, you will find all the
dependencies downloaded and build in the _deps_ directory.

As you see, there is much more Erlang code produce at ProcessOne and
contributed to the Erlang community than just ejabberd repository.

## ejabberd contributions

This is not dependencies, but simply modules that you may find nice to
add to your ejabberd deployment.

We attempted to gather some of the more useful ejabberd modules in a
contribution repository to ease discovery.

This repository is available on Github:
[ejabberd-contribs](https://github.com/processone/ejabberd-contrib)

We are thinking about a better approach for ejabberd contributions
discovery. More on that soon.