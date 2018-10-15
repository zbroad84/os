# RancherOS

The smallest, easiest way to run Docker in production at scale.  Everything in RancherOS is a container managed by Docker.  This includes system services such as udev and rsyslog.  RancherOS includes only the bare minimum amount of software needed to run Docker.  This keeps the binary download of RancherOS very small.  Everything else can be pulled in dynamically through Docker.

## How this works

Everything in RancherOS is a Docker container.  We accomplish this by launching two instances of
Docker.  One is what we call the system Docker which runs as the first process.  System Docker then launches
a container that runs the user Docker.  The user Docker is then the instance that gets primarily
used to create containers.  We created this separation because it seemed logical and also
it would really be bad if somebody did `docker rm -f $(docker ps -qa)` and deleted the entire OS.

![How it works](./rancheros.png "How it works")

## Release

- **Latest: v1.4.1 - Docker 18.03.1-ce - Linux 4.14.67**
- **Stable: v1.4.1 - Docker 18.03.1-ce - Linux 4.14.67**

### ISO

- https://releases.rancher.com/os/latest/rancheros.iso
- https://releases.rancher.com/os/v1.4.1/rancheros.iso

### Additional Downloads

#### Latest Links

* https://releases.rancher.com/os/latest/initrd
* https://releases.rancher.com/os/latest/iso-checksums.txt
* https://releases.rancher.com/os/latest/rancheros-openstack.img
* https://releases.rancher.com/os/latest/rancheros-digitalocean.img
* https://releases.rancher.com/os/latest/rancheros-cloudstack.img
* https://releases.rancher.com/os/latest/rancheros-aliyun.vhd
* https://releases.rancher.com/os/latest/rancheros.ipxe
* https://releases.rancher.com/os/latest/rancheros-gce.tar.gz
* https://releases.rancher.com/os/latest/rootfs.tar.gz
* https://releases.rancher.com/os/latest/vmlinuz
* https://releases.rancher.com/os/latest/rancheros-vmware.iso

#### v1.4.1 Links

* https://releases.rancher.com/os/v1.4.1/initrd
* https://releases.rancher.com/os/v1.4.1/iso-checksums.txt
* https://releases.rancher.com/os/v1.4.1/rancheros-openstack.img
* https://releases.rancher.com/os/v1.4.1/rancheros-digitalocean.img
* https://releases.rancher.com/os/v1.4.1/rancheros-cloudstack.img
* https://releases.rancher.com/os/v1.4.1/rancheros-aliyun.vhd
* https://releases.rancher.com/os/v1.4.1/rancheros.ipxe
* https://releases.rancher.com/os/v1.4.1/rancheros-gce.tar.gz
* https://releases.rancher.com/os/v1.4.1/rootfs.tar.gz
* https://releases.rancher.com/os/v1.4.1/vmlinuz
* https://releases.rancher.com/os/v1.4.1/rancheros-vmware.iso

#### ARM Links

* https://releases.rancher.com/os/latest/rootfs_arm64.tar.gz
* https://releases.rancher.com/os/latest/rancheros-raspberry-pi64.zip
* https://releases.rancher.com/os/v1.4.1/rootfs_arm64.tar.gz
* https://releases.rancher.com/os/v1.4.1/rancheros-raspberry-pi64.zip

**Note**: you can use `http` instead of `https` in the above URLs, e.g. for iPXE.

### Amazon

SSH keys are added to the **`rancher`** user, so you must log in using the **rancher** user.

**HVM**

Region | Type | AMI
-------|------|------
ap-south-1 | HVM | [ami-04d97a73fdcdabe8e](https://ap-south-1.console.aws.amazon.com/ec2/home?region=ap-south-1#launchInstanceWizard:ami=ami-04d97a73fdcdabe8e)
eu-west-3 | HVM | [ami-08f45f3779ca44473](https://eu-west-3.console.aws.amazon.com/ec2/home?region=eu-west-3#launchInstanceWizard:ami=ami-08f45f3779ca44473)
eu-west-2 | HVM | [ami-0b5a34a6083949cc7](https://eu-west-2.console.aws.amazon.com/ec2/home?region=eu-west-2#launchInstanceWizard:ami=ami-0b5a34a6083949cc7)
eu-west-1 | HVM | [ami-0c728496e40cbbfe1](https://eu-west-1.console.aws.amazon.com/ec2/home?region=eu-west-1#launchInstanceWizard:ami=ami-0c728496e40cbbfe1)
ap-northeast-2 | HVM | [ami-064ddff6473c71358](https://ap-northeast-2.console.aws.amazon.com/ec2/home?region=ap-northeast-2#launchInstanceWizard:ami=ami-064ddff6473c71358)
ap-northeast-1 | HVM | [ami-04bbdaca8d13e10de](https://ap-northeast-1.console.aws.amazon.com/ec2/home?region=ap-northeast-1#launchInstanceWizard:ami=ami-04bbdaca8d13e10de)
sa-east-1 | HVM | [ami-0f0bb79a2bba86d08](https://sa-east-1.console.aws.amazon.com/ec2/home?region=sa-east-1#launchInstanceWizard:ami=ami-0f0bb79a2bba86d08)
ca-central-1 | HVM | [ami-04182ecaef9229e34](https://ca-central-1.console.aws.amazon.com/ec2/home?region=ca-central-1#launchInstanceWizard:ami=ami-04182ecaef9229e34)
ap-southeast-1 | HVM | [ami-0fbd73c274a69b114](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#launchInstanceWizard:ami=ami-0fbd73c274a69b114)
ap-southeast-2 | HVM | [ami-083381ed58ee6b977](https://ap-southeast-2.console.aws.amazon.com/ec2/home?region=ap-southeast-2#launchInstanceWizard:ami=ami-083381ed58ee6b977)
eu-central-1 | HVM | [ami-0155d2d2fef357438](https://eu-central-1.console.aws.amazon.com/ec2/home?region=eu-central-1#launchInstanceWizard:ami=ami-0155d2d2fef357438)
us-east-1 | HVM | [ami-9d8293e6](https://aws.amazon.com/marketplace/pp/B01AB05EEA?ref=cns_srchrow)
us-east-2 | HVM | [ami-05b7deb6b4d12a114](https://us-east-2.console.aws.amazon.com/ec2/home?region=us-east-2#launchInstanceWizard:ami=ami-05b7deb6b4d12a114)
us-west-1 | HVM | [ami-0055d680575e2ec03](https://us-west-1.console.aws.amazon.com/ec2/home?region=us-west-1#launchInstanceWizard:ami=ami-0055d680575e2ec03)
us-west-2 | HVM | [ami-08ca2e89d91d17cfe](https://us-west-2.console.aws.amazon.com/ec2/home?region=us-west-2#launchInstanceWizard:ami=ami-08ca2e89d91d17cfe)
cn-north-1 | HVM | [ami-00fcdc82b09cb88a0](https://cn-north-1.console.amazonaws.cn/ec2/home?region=cn-north-1#launchInstanceWizard:ami=ami-00fcdc82b09cb88a0)
cn-northwest-1 | HVM | [ami-079ddb61f42d0a298](https://cn-northwest-1.console.amazonaws.cn/ec2/home?region=cn-northwest-1#launchInstanceWizard:ami=ami-079ddb61f42d0a298)

Additionally, images are available with support for Amazon EC2 Container Service (ECS) [here](https://rancher.com/docs/os/v1.x/en/installation/amazon-ecs/#amazon-ecs-enabled-amis).

### Google Compute Engine

We are providing a disk image that users can download and import for use in Google Compute Engine. The image can be obtained from the release artifacts for RancherOS.

[Download Latest Image](https://releases.rancher.com/os/latest/rancheros-gce.tar.gz)

[Download Stable Image](https://releases.rancher.com/os/v1.4.1/rancheros-gce.tar.gz)

Please follow the directions at our [docs to launch in GCE](https://rancher.com/docs/os/v1.x/en/installation/running-rancheros/cloud/gce/).

## Documentation for RancherOS

Please refer to our [RancherOS Documentation](https://rancher.com/docs/os/v1.x/en/) website to read all about RancherOS. It has detailed information on how RancherOS works, getting-started and other details.

## Support, Discussion, and Community
If you need any help with RancherOS or Rancher, please join us at either our [Rancher forums](http://forums.rancher.com) or [#rancher IRC channel](http://webchat.freenode.net/?channels=rancher) where most of our team hangs out at.

For security issues, please email security@rancher.com instead of posting a public issue in GitHub.  You may (but are not required to) use the GPG key located on [Keybase](https://keybase.io/rancher).


Please submit any **RancherOS** bugs, issues, and feature requests to [rancher/os](//github.com/rancher/os/issues).

Please submit any **Rancher** bugs, issues, and feature requests to [rancher/rancher](//github.com/rancher/rancher/issues).

## License

Copyright (c) 2014-2018 [Rancher Labs, Inc.](http://rancher.com)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
