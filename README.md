# NetApp Ansible Playbooks

#### Date: 3-10-2019
#### Version: 1.0


## Description

Contained within this repository are NetApp Ansible playbooks


## Prerequisites

Ansible 2.4.2 or above

Python 2.7.12 or above


## Configure Ansible to work with NetApp


The following steps will help you install the updated Ansible modules into your Ansible system.

```sh

git clone https://github.com/NetApp/ansible.git

cd ansible

ansible --version

```

Your output might differ but it will look something like this:
ansible 2.7.12

```

config file = /etc/ansible/ansible.cfg

configured module search path = /root/.ansible/plugins/modules, /usr/share/ansible/plugins/modules

ansible python module location = /usr/local/lib/python2.7/dist-packages/ansible

executable location = /usr/local/bin/ansible

```

python version = 2.7.12 (default, Nov 20 2017, 18:23:56) [GCC 5.4.0 20160609]

The line that starts with “ansible python module location” shows you where your local modules are so replace your path if different for the export command


```sh

export ANSIBLE_PATH=/usr/local/lib/python2.7/dist-packages/ansible

cp -aRv lib/ansible/module_utils/netapp* $ANSIBLE_PATH/module_utils/

cp -aRv lib/ansible/modules/storage/netapp/* $ANSIBLE_PATH/modules/storage/netapp/


```

#### Finally, these modules use http by default for communication.  You will need to enable it on the ONTAP system.


```sh

cluster::> set -privilege advanced

cluster::> system services web modify -http-enabled true

```

#### Note: Configuration might differ from version to version

Incase if you ran into issues with NetApp python modules you need to manually import them


```
pip install netapp-lib

import netapp_lib ---> in the python shell
```
