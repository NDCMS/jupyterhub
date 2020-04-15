.. Jupyterhub-earth documentation master file, created by
   sphinx-quickstart on Wed Apr 15 09:11:21 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Jupyterhub-earth's documentation!
============================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

Jupyterhub Service on Earth
***************************

This service can be accessed via https://earth.crc.nd.edu:49000

Users need an account on this login node at the CRC.

Frequently Asked Questions
===========================

1. Jupyter notebook database issues

If you get the following error::

    Unexpected error while saving file: coffea_tests/Untitled.ipynb database disk image is malformed

a. Log out of jupyterhub, so that the following process disappears
b. Then, SSH into earth and run::

    $ mv ~/.local/share/jupyter{,.bak}
    $ mv ~/.ipython{,.bak}

c. Come back to your browser and try again.

2. AFS issues

The error::

    "Spawn failed: Server at http://127.0.0.1:35083/user/btovar/ didn't respond in 30 seconds"

This could be related to AFS tokens, if jupyter logs (you can ask earth's system administrator for this) look like this::
    
    Apr 14 15:29:36 earth bash: [I 2020-04-14 15:29:36.700 JupyterHub pages:303] btovar is pending spawn
    Apr 14 15:29:36 earth bash: [I 2020-04-14 15:29:36.702 JupyterHub log:174] 200 GET /hub/spawn-pending/btovar (btovar@10.63.2.130) 15.99ms
    Apr 14 15:29:36 earth bash: PermissionError: [Errno 13] Permission denied: '/afs/crc.nd.edu/user/b/btovar/.jupyter/migrated'
    Apr 14 15:29:45 earth bash: tornado.web.HTTPError: HTTP 500: Internal Server Error (Spawner failed to start [status=1]. The logs for btovar may contain details.)

The solution is:

a. Logout from the current session
b. Re-login
c. Go to the "Token" tab
d. Remove all current tokens
e. Go to "Home" tab
f. Click on "Start my server"
