(http://socrates.io/#xfL9riN)

# Stop trying to glue your services together`; import lymph`

> A talk for EuroPython 2015 by Alejandro Castillo & Max Brauer

Hello and good afternoon. Hopefully you've had a nice lunch. My name is
Castillo / Max and I'd like to introduce you to _lymph_, a framework for
writing services in Python. With lymph you can write services with almost no
boilerplate. But let me introduce us first.

We're Delivery Hero, a holding of online food ordering service world-wide.
We're located in Berlin.  We operate in 34 countries and growing. Let me
explain the concept of online food ordering to those who're unfamiliar with it.
However, I doubt there arent any ;) The concept it's simple: get hungry, go
online, search for restaurants close to you, compile your order, pay online,
wait for the delivery. Basically, it's e-commerce with very grumpy customers.
But the restaurant integration, e.g. order transmission, fulfillment, delivery,
etc. offer quite an ecosystem of things to tackle.

For the sake of this talk we assume that you're familiar with the concept of
services. We will not discuss the differences between monoliths and services
and the individual leverages and drawbacks. By the way, how many of you have
attended the nice talk about the 'nameko' framework?

So, the first thing some of you would be thinking is 'why build a framework?'.
The answer was that when we looked around we did not find anything that would
fit our neccesities. We wanted to work with services but we wanted some very
specific things. We are mainly python powered so we wanted to stay inside
python as much as possible. We wanted to abstract away all the problems one has
to consider when dealing with service (transporting data, registering services,
discovering them), we wanted to enable our developer to work with services in a
simple and easy way, no boilerplate, no excessive details that don't relate to
bussiness logic. Yes, some of you will be thinking after their nice talk 'use
Nameko'. But that was not in the current state when we started and anyway it
does not cover all the things we wanted to get from our framework.

So, say hello to lymph. By now you must be itching to see how a service looks
in lymph. Spoiler alert, very much like in nameko.

[Show simple echo service]

One of the first things we considered when building lymph was the tooling. We
think we managed to get some very nice tooling built around it to make
development of services easier.

### Introduction
* Hello
* this is who we are
* company
* this is what we do
* what is this (what is lymph in a nutshell)
* why are we doing this (reasons)

### lymph
* sample (with local events and static registry)
 * introduce sample services / scenario
 * show them(code) and explain them
 * introduce echo
 * configure it
 * show tooling (run it, discover and inspect)
 * make a request
 * introduce listener
 * show tooling (run it, discover (and inspect))
 * (run more than one instance)
 * make a request
 * emit events, subscribe
 * introduce web
 * curl
 * show traceid in logs
* show sample with rabbitmq and zk
 * proves claim

### high-level architecture
* greenlets
* rpc via 0mq
* events via rabbitmq (pluggable)
* registry via zk (pluggable)
* http with werkzeug
* testing
* TestCases

### compare with nameko
* (http://lucumr.pocoo.org/2015/4/8/microservices-with-nameko/)
* tech
* running
* testing

### future
* eco system (storage, storeproxy, flow etc)
* distconfig

### summary and outro
* lymph.io
* we accept PRs
* we're hiring

### QA
 
### nice-to-have
* plugins (lymph-top, newrelic, sentry)
* monitoring
* serial events & broadcast(websockets)

# Setup

create virtualenv:
```
virtualenv venv
. venv/bin/activate
pip install -r requirements.txt
```

install tmuxinator:
```
brew install tmuxinator
```

make sure `$EDITOR` is set:
```
mux doctor
```

link tmuxinator projects:
```
ln -s `pwd`/tmuxinator/* ~/.tmuxinator
```

remove zookeeper node `/lymph`:
```
zkCli.sh
rmr /lymph
```

make sure zk and rabbitmq are running. start tmuxinator project:
```
mux start all
```
