# openstack-octavia-amphora-image

Pipeline for building [OpenStack Octavia](https://docs.openstack.org/octavia/latest/reference/introduction.html) amphora images.

## Build

### Development

Prepare environment:
```sh
# create venv
python3 -m venv venv
# activate venv
source venv/bin/activate
# install requirements
pip install -r requirements.txt
sudo apt install -y qemu-utils git kpartx debootstrap
# clone octavia
git clone -b stable/2024.1 https://opendev.org/openstack/octavia
```

Build image:
```sh
octavia/diskimage-create/diskimage-create.sh \
    -a amd64 -i ubuntu-minimal -d jammy \
    -o amphora-x64-haproxy.qcow2
```

### GitHub Workflow

![build-image](https://github.com/nimbolus/openstack-octavia-amphora-image/actions/workflows/build.yml/badge.svg)

Go to [Actions](https://github.com/nimbolus/openstack-octavia-amphora-image/actions/workflows/build.yml) and click on `Run workflow`.

Images can be downloaded from job artifacts.
