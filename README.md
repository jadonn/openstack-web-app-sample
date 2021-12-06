# Deployment Samples

This repo contains sample deployments of cloud infrastructure using OpenStack as the cloud platform and Ansible as the deployment tool.

## Install Ansible and OpenStack SDK
Before you can run the Ansible playbooks in this repo, you have to install Ansible and the generic OpenStack SDK. I recommend creating a `venv` virtual environment and using `pip` to install Ansible and the generic OpenStack SDK.

### Setup venv virtual environment

You can setup a `venv` virtual environment in the current directory on Linux in a reasonably modern distribution by using the following command:

    python3 -m venv venv

If successful, this command will not show any output. This command will use python3 to create a `venv` virtual environment inside of the current directory in a folder called *venv*. The virtual environment will contain a full copy of the system's Python installation that is fully isolated from the system's Python isolation. Using `venv` virtual environments is generally considered a best practice since it isolates your dependencies from your system's Python installation.

### Activate your venv virtual environment

Before you install any dependencies, activate your `venv` virtual environment. You can use the following command on Linux to activate the `venv` virtual environment if you are in the same directory as the `venv` folder you created in the previous step:

    source ./venv/bin/activate

This command will tell your shell/terminal session to use the Python installation inside of `./venv/bin/` for everything you do with Python instead of the system's default Python installation. This will ensure you do not install packages into your system's main Python installation.\
\
If the command runs successfully, you should see your terminal change to show `(venv)` at the start of each input line. It will like something like this:

    (venv) [yourUser@yourComputer]$

The `(venv)` at the beginning of the line means that the Python installation inside of the `venv` folder has been activated and is currently in use. You can safely install software into the virtual Python environment. You can continue to use Python commands as you normally would; the commands you use will seamlessly use the virtual Python environment instead of the system Python installation.

### Update pip to the latest version

Pip is Python's built-in package installer for managing dependencies. Depending on your Linux distribution, you will probably have an older version of Python and Pip installed. Some packages will not install if Pip is not the latest version available. You can use the `pip` command to update Pip to the latest version. Run the following command to update Pip:

    pip install -U pip

This command will tell Pip to download the new Pip package and install it in place of the current Pip package. The output from the command looks something like the following output:

```
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 20.2.2
    Uninstalling pip-20.2.2:
      Successfully uninstalled pip-20.2.2
Successfully installed pip-21.3.1
```

Your output may vary a little bit based on what version of Pip you had installed and what version is installed.

### Install Ansible and the OpenStack SDK using Pip

After you have updated Pip to the most recent version of Pip, you can install Ansible and the OpenStack SDK using Pip. Run the following command to install Ansible and the OpenStack SDK:

    pip install ansible openstacksdk

This command will install Ansible, the OpenStack SDK, and any supporting packages they require. The output from the command should look something like this:

```
Collecting ansible
  Downloading ansible-5.0.0.tar.gz (38.4 MB)
     |████████████████████████████████| 38.4 MB 4.5 MB/s            
  Preparing metadata (setup.py) ... done
Collecting openstacksdk
  Using cached openstacksdk-0.60.0-py3-none-any.whl (1.4 MB)
Collecting ansible-core<2.13,>=2.12.0
  Downloading ansible-core-2.12.0.tar.gz (7.4 MB)
     |████████████████████████████████| 7.4 MB 4.8 MB/s            
  Preparing metadata (setup.py) ... done
Collecting dogpile.cache>=0.6.5
  Using cached dogpile.cache-1.1.4-py3-none-any.whl (50 kB)
Collecting decorator>=4.4.1
  Using cached decorator-5.1.0-py3-none-any.whl (9.1 kB)
Collecting requestsexceptions>=1.2.0
  Using cached requestsexceptions-1.4.0-py2.py3-none-any.whl (3.8 kB)
Collecting appdirs>=1.3.0
  Using cached appdirs-1.4.4-py2.py3-none-any.whl (9.6 kB)
Collecting keystoneauth1>=3.18.0
  Using cached keystoneauth1-4.4.0-py3-none-any.whl (314 kB)
Collecting netifaces>=0.10.4
  Using cached netifaces-0.11.0-cp39-cp39-manylinux_2_5_x86_64.manylinux1_x86_64.whl (32 kB)
Collecting jsonpatch!=1.20,>=1.16
  Using cached jsonpatch-1.32-py2.py3-none-any.whl (12 kB)
Collecting cryptography>=2.7
  Downloading cryptography-36.0.0-cp36-abi3-manylinux_2_24_x86_64.whl (3.6 MB)
     |████████████████████████████████| 3.6 MB 5.2 MB/s            
Collecting jmespath>=0.9.0
  Using cached jmespath-0.10.0-py2.py3-none-any.whl (24 kB)
Collecting pbr!=2.1.0,>=2.0.0
  Using cached pbr-5.8.0-py2.py3-none-any.whl (112 kB)
Collecting iso8601>=0.1.11
  Using cached iso8601-1.0.2-py3-none-any.whl (9.7 kB)
Collecting os-service-types>=1.7.0
  Using cached os_service_types-1.7.0-py2.py3-none-any.whl (24 kB)
Collecting PyYAML>=3.13
  Using cached PyYAML-6.0-cp39-cp39-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_12_x86_64.manylinux2010_x86_64.whl (661 kB)
Collecting munch>=2.1.0
  Using cached munch-2.5.0-py2.py3-none-any.whl (10 kB)
Collecting jinja2
  Using cached Jinja2-3.0.3-py3-none-any.whl (133 kB)
Collecting packaging
  Using cached packaging-21.3-py3-none-any.whl (40 kB)
Collecting resolvelib<0.6.0,>=0.5.3
  Using cached resolvelib-0.5.4-py2.py3-none-any.whl (12 kB)
Collecting cffi>=1.12
  Using cached cffi-1.15.0-cp39-cp39-manylinux_2_12_x86_64.manylinux2010_x86_64.whl (444 kB)
Collecting stevedore>=3.0.0
  Using cached stevedore-3.5.0-py3-none-any.whl (49 kB)
Collecting jsonpointer>=1.9
  Using cached jsonpointer-2.2-py2.py3-none-any.whl (7.5 kB)
Collecting six>=1.10.0
  Using cached six-1.16.0-py2.py3-none-any.whl (11 kB)
Collecting requests>=2.14.2
  Using cached requests-2.26.0-py2.py3-none-any.whl (62 kB)
Collecting pycparser
  Using cached pycparser-2.21-py2.py3-none-any.whl (118 kB)
Collecting idna<4,>=2.5
  Using cached idna-3.3-py3-none-any.whl (61 kB)
Collecting certifi>=2017.4.17
  Using cached certifi-2021.10.8-py2.py3-none-any.whl (149 kB)
Collecting charset-normalizer~=2.0.0
  Using cached charset_normalizer-2.0.8-py3-none-any.whl (39 kB)
Collecting urllib3<1.27,>=1.21.1
  Using cached urllib3-1.26.7-py2.py3-none-any.whl (138 kB)
Collecting MarkupSafe>=2.0
  Downloading MarkupSafe-2.0.1-cp39-cp39-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_12_x86_64.manylinux2010_x86_64.whl (30 kB)
Collecting pyparsing!=3.0.5,>=2.0.2
  Using cached pyparsing-3.0.6-py3-none-any.whl (97 kB)
Using legacy 'setup.py install' for ansible, since package 'wheel' is not installed.
Using legacy 'setup.py install' for ansible-core, since package 'wheel' is not installed.
Installing collected packages: pycparser, urllib3, pyparsing, pbr, MarkupSafe, idna, charset-normalizer, cffi, certifi, stevedore, six, resolvelib, requests, PyYAML, packaging, os-service-types, jsonpointer, jinja2, iso8601, decorator, cryptography, requestsexceptions, netifaces, munch, keystoneauth1, jsonpatch, jmespath, dogpile.cache, appdirs, ansible-core, openstacksdk, ansible
    Running setup.py install for ansible-core ... done
    Running setup.py install for ansible ... done
Successfully installed MarkupSafe-2.0.1 PyYAML-6.0 ansible-5.0.0 ansible-core-2.12.0 appdirs-1.4.4 certifi-2021.10.8 cffi-1.15.0 charset-normalizer-2.0.8 cryptography-36.0.0 decorator-5.1.0 dogpile.cache-1.1.4 idna-3.3 iso8601-1.0.2 jinja2-3.0.3 jmespath-0.10.0 jsonpatch-1.32 jsonpointer-2.2 keystoneauth1-4.4.0 munch-2.5.0 netifaces-0.11.0 openstacksdk-0.60.0 os-service-types-1.7.0 packaging-21.3 pbr-5.8.0 pycparser-2.21 pyparsing-3.0.6 requests-2.26.0 requestsexceptions-1.4.0 resolvelib-0.5.4 six-1.16.0 stevedore-3.5.0 urllib3-1.26.7
```

If everything installed successfully, you should be able to run the `ansible` and `ansible-playbook` commands.

## Install the OpenStack Cloud collection using Ansible Galaxy
Ansible Galaxy is the public repository of Ansible playbooks and resources that Ansible users can download and use for free. When you installed Ansible, the `ansible-galaxy` tool was also installed. You can use the `ansible-galaxy` command to install resources users have uploaded to the central Ansible Galaxy service. Ansible Galaxy has a collection of playbooks to manage infrastructure on OpenStack private clouds. Run the following command to install the OpenStack Cloud collection from Ansible Galaxy:

    ansible-galaxy collection install openstack.cloud

This command will download the collection of playbooks under the name `openstack.cloud` into your local environment from Ansible Galaxy. The output will look something like:

```
Starting galaxy collection install process
Process install dependency map
Starting collection install process
Downloading https://galaxy.ansible.com/download/openstack-cloud-1.5.3.tar.gz to /home/yourUser/.ansible/tmp/ansible-local-657174im5m2tif/tmps25d8cyu/openstack-cloud-1.5.3-4w7dxllq
Installing 'openstack.cloud:1.5.3' to '/home/yourUser/.ansible/collections/ansible_collections/openstack/cloud'
openstack.cloud:1.5.3 was installed successfully
```

At this point you can use the OpenStack Cloud collection inside of your Ansible playbooks, but you still have to define a `clouds.yml` file that gives Ansible the information it needs to communicate with your OpenStack cloud.

## Create a clouds.yml file

The clouds.yml (or clouds.yaml) file defines the information that the OpenStack Cloud collection will use to communicate with your OpenStack cloud. An example minimal clouds.yml file would look like this:

```
clouds:
  yourcloud:
    auth:
      auth_url: http://your_auth_url
      project_name: yourProject
      username: yourUser
      password: yourPassword
    region_name: yourRegion
    user_domain_name: Default
    project_domain_name: Default
```

This is a very basic minimal clouds.yml file, but all of these values have to be defined or your playbook runs will fail with authentication errors. If you follow this example, the clouds.yml file would have sensitive information. Never share files that have user credentials like this or commit these files into your version control.

## 