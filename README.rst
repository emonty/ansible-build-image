Ansible Role: build-image
=========================

Build disk images for OpenStack clouds

Requirements
------------

diskimage-builder

If you want to build VHD images, you'll want the vhd-util package from
the ppa:openstack-ci-core/vhd-util PPA.

Role Variables
--------------

distro: The logical name  of the distro to use for the base of the image

release: The release of the distro to use

elements: List of additional elements to append (optional)

elements_path: List of paths on which to find elements (optional)

image_outdir: Directory in which to place built images (optional, defaults to
              /var/lib/dib-images)

image_tmpdir: Directory to use for image conversions (should be large,
              defaults to /tmp)

formats: List of image output formats (optional, defaults to [qcow2])

qemu_image_options: Options to pass to qemu-image (optional, defaults to
                    "compat=0.10")

Example Playbook
----------------

.. code-block:: yaml

  - hosts: localhost
    roles:
    - role: build-image
      distro: ubuntu
      release: trusty
      elements: infra
      elements_path: /opt/project-config/nodepool/elements
      formats:
      - vhd
      - qcow2

License
-------

Apache

Author Information
------------------

build-image is maintained by the OpenStack Infra team. The best way to
contact them is on #openstack-infra on freenode.
