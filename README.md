# The NerdyNik Ansible Galaxy

This is a collection of Ansible Roles that I have created over the years for setting up varies applications and infrastructure within my Homelab, as well as assist with rebuilding my own workstations.

## The Collections

All collections contained here are part of the `nerdynik` Namespace. Each collection contains roles, plugins, etc that revolve around the governing collection's focus.

### `general` Collection

A collection of general purpose roles that are used by other roles within the namespace.
See the [README](general/README.md) for details on each role.

### `workstation` Collection

A collection of roles that focus around setting up applications and other items on MacOS and Linux based workstations. 
Think applications and configs that you might use in your development workstation, or in some cases gaming.
See the [README](workstation/README.md) for details on each role.

### `host` Collection

A collection of roles that focus around either installing applications, configuring systems, or laying the ground work
for other layers (eg K8s/Kubernetes) upon baremetal or VM systems. See the [README](host/README.md) for details on each role.

### `k8s` Collection

A collection of roles focusing around installing applications within a K8s cluster/environment.
Most leverage `kubectl` based deployment using Jinja2 template to generate the deployment. 
While others use Helm Charts to deploy applications, or will use Helm Charts in conjunction to the `kubectl` approach.
See the [README](host/README.md) for details on each role.


# How to use

There are 2 common ways to install Ansible Collections, CLI and `requirements.yml` file. Here we will show the 2 approaches in relation to both collection contained here. You can also read more about installing Ansible Collections from Git in the 
[Ansible Docs](https://docs.ansible.com/) on
[Installing Collections from Git](https://docs.ansible.com/projects/ansible/latest/collections_guide/collections_installing.html#installing-a-collection-from-a-git-repository)

## Installing via CLI

You can use the `ansible-galaxy` cli command to install any/all of these collections. 
While this can be the easiest way to leverage any of these roles in your projects, it's not the best way. 
See the *Installing via `requirements.yml` file* section for more details.

### Installing Globally for All Projects

In this example, the selected collection will be install in typically your `~/.ansible/collections/ansible_collections` folder.
You can run the following command to see all the default paths where collections may get install: `ansible-config dump | grep COLLECTIONS_PATHS`.
See the Ansible docs on [Collection Installing](https://docs.ansible.com/projects/ansible/latest/collections_guide/collections_installing.html) for more details.

```bash
# Workstation Collection
ansible-galaxy collection workstation install git+https://github.com/nerdynick/ansible-galaxy

# General Collection
ansible-galaxy collection general install git+https://github.com/nerdynick/ansible-galaxy
```

### Installing Relative to You Project

If you prefer to make them only available to a specific project. You can install them adjacent to the playbooks of you project with the following 2 steps.
You can also read more about this approach in the Ansible docs (Installing Collections Adjacent to Playbooks)[https://docs.ansible.com/projects/ansible/latest/collections_guide/collections_installing.html#installing-collections-adjacent-to-playbooks].

#### Step 1 - Setup Project

If you don't have it already created you will need to create an `ansible.cfg` file within the root, where all your playbooks are typically located, of your project. Within that file you can either copy+paste the below or ensure that the `collections_paths` config has been added to your `[defaults]` section.

```ini
[defaults]
collections_path = ./collections
```

#### Step 2 - Install the Collection(s)

```bash
cd /path/to/my/project
ansible-galaxy collection workstation install git+https://github.com/nerdynick/ansible-galaxy -p ./collections
```

## Installing via `requirements.yml` file

You can read more on this in the [Ansible Docs](https://docs.ansible.com/) on [Installing Multiple Collects with requirements file](https://docs.ansible.com/projects/ansible/latest/collections_guide/collections_installing.html#install-multiple-collections-with-a-requirements-file)

### Step 1 - Create your `requirements.yml` file

If you haven't done so already, create a file called `requirements.yml` within the root of your ansible project. 

### Step 2 - Add respective contents

Within your `requirements.yml` file you will need to add a `collections` section that will house a list of all the collections that need to be installed as part of your Ansible Projects dependency requirements.

**Example**
```yml
collections:
    # Homelab
    - name: https://github.com/nerdynick/ansible-galaxy.git#/general/
      version: main # Can be a branch or specific commit
      type: git

    # Workstation
    - name: https://github.com/nerdynick/ansible-galaxy.git#/workstation/
      version: main # Can be a branch or specific commit
      type: git

    # Install all collections from this repo
    - name: https://github.com/nerdynick/ansible-galaxy.git
      version: main # Can be a branch or specific commit
      type: git
```

### Step 3 - Install All the Collections

Once you have your `requirements.yml` file all setup. You just simply need to run the `ansible-galaxy` command with a few options to install.

```bash
#Install all collections globally
ansible-galaxy collections install -f requirements.yml

#Install all collections local to the project
ansible-galaxy collections install -f requirements.yml -p ./collections
```