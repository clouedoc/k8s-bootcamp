# week 2 - create your cluster

## Criterions for success

You can consider this exercice as a success if you can tick all the following boxes:

- [ ] You have created a Hetzner cloud account, project and corresponding API token
- [ ] You have created your own cluster using `hetzner-k3s`; which resulted in a kubeconfig.yaml
- [ ] You managed to access your cluster using `kubectl`

## Exercice

In today's exercice, you will be walked through the creation of your own little Kubernetes cluster.
It costs a bit to maintain (about 10$/month), so you'll need at least that much money in your bank account.

The provider I've chosen is Hetzner Cloud since it's the one with the best price/quality ratio.

### Step 1: create a Hetzner Cloud account

1. Create an account here: <https://www.hetzner.com/cloud>
2. Make sure that you can access your projects dashboard here: <https://console.hetzner.cloud/projects>

### Step 2: creating a project for your k8s cluster

one k8s cluster = one project

1. Create a new project
2. Give it a cool name (e.g. "skynet")
3. Go inside your project and manually create a small server. Is Hetzner allowing you to do so?
4. Delete your testing server; we don't need it.

### Step 3: creating your cluster

1. Head over to [hetzner-k3s's repo](https://github.com/vitobotta/hetzner-k3s) and install the CLI utility
2. Run `hetzner-k3s` to make sure that it's installed
3. Create your very-own `clusterdef.yaml` file inside this folder. Make sure that you understand every parameters. (a sample one is included here - you'll also need to get your own Hetzner Cloud API key)
4. Create your cluster with `hetzner-k3s create -f clusterdef.yaml`; if there are errors: fix them! This will produce a `kubeconfig.yaml`

### Step 4: access your cluster with your KUBECONFIG

1. Copy the `kubeconfig.yaml` file to your `~/.kube/config` file
2. List your nodes with `kubectl get nodes` -- is there something showing up here?
3. List your pods with `kubectl get pods --all-namespaces`

If everything's alright, then congrats, you've got your own cluster up and running!

While it's small right now, you'll be able to scale it up later on.

The beauty of k8s is that if you write your software smartly, you'll be able to scale it up to infinity by changing a number in a config file. The drawback is that you'll need to conceive your software smartly.

### Step 5: destroy your cluster (optional)

If you want to save some money, you can destroy your cluster with `hetzner-k3s delete -f clusterdef.yaml`.

You'll need to create it again next week, though.
