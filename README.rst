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

And edit away. You provice a list of projects. A typical entry might look like
this::

    projects:
      - name: example

        repo:
          type: git
          url: git://github.com/Jc2k/sidekick-example

        on-failure: rollback
        on-success: leave-running

The following attributes are supported:

name
    The name of the project. This must be unique to this caroline instance.
repo
    Configuration information for source code access.
on-failure
    What to do if a deployment fails. (See Handling Failure).
on-success
    What do do when a deployment succeeds. (See Handling Success).


Source Code Mgmt
================

Each project should define a 'repo'. It is expected that the Sidekick
file will be in the root of that repository's master branch.

Currently the repository variables are:

type
    Set to 'git' for Git and 'svn' for Suversion.
url
    The path to the root of the repository. For Subversion, this is
    the folder below trunk.


Handling Failure
================

The 'on-failure' option can be set to one of several values to control how
Caroline deals with failed deployments.

The default behaviour is to rollback to the last snapshot. You can explicitly
set this behaviour with 'rollback'. This requires a sidekick environment that
supports snapshots, like VMWare.

You might be using a backend that doesn't support snapshots, or you would
prefer to start from scartch after a failure. For that, you can set 'on-failure'
to 'destroy'.

You might want to test your Yaybu cookbooks ability to deal with recovering
from failure. You can, therefore, set 'on-failure' to 'leave-running'.


Handling Success
=================

The default behaviour on success is to leave the VM running in the state it
was in after deployment ('leave-running'). By setting the 'on-success'
setting for a project you can make it 'rollback' or 'destroy' too.


Why Caroline?
=============

We needed a name. Names are hard, and theres so much testing to be done...
Caroline may change if we every come up with something better.

