Mellanox NEO SDN Controller
===========================

This role can be used to configure a Mellanox NEO SDN controller running in a
Docker container.

Tooling to build a compatible container image is provided on `Github
<https://github.com/stackhpc/docker-mlnx-neo>`.

Requirements
------------

The host executing the role has the following requirements:

* Docker engine
* Python ``docker >= 2.0.0``

Role Variables
--------------

* ``mlnx_neo_action``: Action to perform. One of ``build``, ``deploy``,
``destroy``, ``pull``, ``reconfigure``, ``upgrade``. Defaults to ``deploy``.
* ``mlnx_neo_enabled``: Whether NEO is enabled. Defaults to ``true``.
* ``mlnx_neo_image``: Docker image name. Required.
* ``mlnx_neo_tag``: Docker image tag. Defaults to ``latest``.
* ``mlnx_neo_image_full``: Full docker image specification.
* ``mlnx_neo_restart_policy``: Docker restart policy for the NEO container.
  Defaults to ``unless-stopped``.
* ``mlnx_neo_restart_retries``: Number of Docker restarts. Defaults to 10.
* ``mlnx_neo_startup_config_path``: Path to a script template on localhost
  containing startup configuration. Default is
  ``/etc/mlnx-neo/mlnx-neo-configure``.
* ``mlnx_neo_config_path``: Path to a directory on the remote host to store
  configuration.  Default is ``/etc/mlnx-neo``.

The following variables are relevant only when ``mlnx_neo_action`` is
``build``:

* ``mlnx_neo_repo_url``: URL of the git repo containing the image. Default is
  ``https://github.com/stackhpc/docker-mlnx-neo``.
* ``mlnx_neo_repo_version``: Version to check out for the git repo containing
  the image. Default is ``master``.
* ``mlnx_neo_repo_checkout_path``: Path to a directory in which to check out
  the git repo. Default is ``/tmp``.
* ``mlnx_neo_tarball_url``: URL of the NEO software tarball. This must be set
  to build the image.
* ``mlnx_neo_push``: Whether to push images after they have been built. Default
  is ``false``.
* ``mlnx_neo_force_rebuild``: Whether to build the image even if an image of
  the same name and tag exists. Default is ``false``.

Dependencies
------------

None

Example Playbook
----------------

The following playbook configures Mellanox NEO.

    ---
    - hosts: mlnx-neo
      roles:
        - role: mlnx-neo

Author Information
------------------

- Mark Goddard (<mark@stackhpc.com>)
