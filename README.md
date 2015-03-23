Ansible Role: build-image
=========================

Build and upload base images to OpenStack clouds

Requirements
------------

diskimage-builder, and infra project-config repo, shade and a properly
configured clouds.yaml file.

You'll also need the vhd-util package from the ppa:mordred/infra PPA.

Role Variables
--------------

```yaml
prefix: A string to preprend to the image name in Glance
distro: The logical name  of the distro to use for the base of the image
elements: Additional elements to append (optional)
elements_path: colon separated path on which to find elements (optional)
qemu_image_options: Options to pass to qemu-image (optional)
image_outdir: Directory in which to place built images
image_tmpdir: Directory to use for image conversions (should be large)
# Looking in vars/main.yml is going to be the best way to grok this next one
clouds: A list of dicts describing the clouds to upload the build image to.
```

Example Playbook
----------------

     - hosts: localhost
       roles:
       - role: build-image
         distro: ubuntu
         release: trusty
         prefix: infra
         elements: infra
         elements_path: /opt/project-config/nodepool/elements
         clouds:
         - name: rackspace
           regions:
           - dfw
           - iad
           - ord
           format: vhd
           properties:
               vm_mode: hvm
               xenapi_use_agent: false
         - name: hp
           regions:
           - region-b

License
-------

Apache

Author Information
------------------

build-image is maintained by the OpenStack Infra team. The best way to
contact them is on #openstack-infra on freenode.
