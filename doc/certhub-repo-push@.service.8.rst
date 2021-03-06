certhub-repo-push@.service
==========================

Synopsis
--------

**certhub-repo-push@.service**

**certhub-repo-push@.path**


Description
-----------

A service which pushes the certhub repository to another host.

A path unit which runs the service unit whenever the master branch of the
local certhub repository is updated.

The unescaped instance name (systemd unescaped instance string specifier
``%I``) is used as the URL for the remote repository. Note that the instance
name likely needs to be escaped using :program:`systemd-escape --template`.


Environment
-----------

.. envvar:: CERTHUB_REPO

   URL of the repository where certificates are stored. Defaults to:
   ``/var/lib/certhub/certs.git``

.. envvar:: CERTHUB_REPO_PUSH_REMOTE

   URL of the remote repository. Defaults to:
   ``CERTHUB_REPO_PUSH_REMOTE=%I``

.. envvar:: CERTHUB_REPO_PUSH_ARGS

   Arguments to the git push command. Defaults to:
   ``--mirror``

.. envvar::  CERTHUB_REPO_PUSH_REFSPEC

   Refspec for the git push command. Empty by default.


Files
-----

.. envfile:: /etc/certhub/env

   Optional environment file shared by all instances and certhub services.

.. envfile:: /etc/certhub/%i.env

   Optional per-instance environment file shared by all certhub services.

.. envfile:: /etc/certhub/certhub-repo-push.env

   Optional per-service environment file shared by all certhub service
   instances.

.. envfile:: /etc/certhub/%i.certhub-repo-push.env

   Optional per-instance and per-service environment file.


See Also
--------

:manpage:`git-push(1)`
