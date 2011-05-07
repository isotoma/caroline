========
Caroline
========

Caroline provides a stock buildbot configuration for teams which use Sidekick.
Caroline will deploy your Sidekick cluster on every commit providing instant
feedback if you introduce problems. Caroline will be your nemesis, watching
you, testing, pointing out your mistakes.


Installation
============

Caroline comes with a simple buildout which installs sidekick and sets up a
buildbot master and slave::

    python bootstrap.py
    ./bin/buildout

You can start, stop, restart and check the status of the master and slave with
the cluster script::

    ./bin/cluster start
    ./bin/cluster restart
    ./bin/cluster status
    ./bin/cluster stop


Configuration
=============

Caroline comes with a simple yay configuration file. Our hope is that you have
to provide as little information as possible beyond a source code repository
and a project name.

For now, you can find it in the root of your caroline directory::

    cp caroline.yay.sample caroline.yay

And edit away.


Why Caroline?
=============

We needed a name. Names are hard, and theres so much testing to be done...
Caroline may change if we every come up with something better.

