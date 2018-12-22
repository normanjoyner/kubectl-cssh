# kubectl-ssh

## About

### Description
A kubectl plugin to SSH into Kubernetes nodes within separate tmux panes

### Installation
Add `kubectl-ssh` to your `$PATH`. For more information about how plugins are loaded, please see the [official documentation](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/).
```
git clone git@github.com:containership/kubectl-ssh.git ~/.kube/plugins/kubectl-ssh
```

### Usage
```
 > kubectl ssh --help
Allows users to SSH into Kubernetes nodes by opening a new tmux pane for each matching node

Options:
  -a, --address-type='ExternalIP': Node address type to query for (e.g. InternalIP/ExternalIP)
  -i, --identity-file='': Selects a file from which the identity (private key) for public key authentication is read
  -l, --selector='': Selector (label query) to filter on, supports '=', '==', and '!='.(e.g. -l key1=value1,key2=value2)
  -p, --port='': SSH port
  -u, --username='': SSH Username

Usage:
  kubectl ssh [flags] [options]
```

### Examples
SSH into all nodes in the cluster:
```
kubectl ssh
```

SSH into master nodes only:
```
kubectl ssh -l node-role.kubernetes.io/master=""
```

SSH into master nodes in private network topologies:
```
kubectl ssh -l "kubernetes.io/role=master" -a "InternalIP"
```
