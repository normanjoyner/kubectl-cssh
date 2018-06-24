# kubectl-tmux-ssh

## About

### Description
A kubectl plugin to ssh into Kubernetes nodes within separate tmux panes

### Installation
Add `kubectl-tmux-ssh` to your `kubectl` plugins directory. For more information about how plugins are loaded, please see the [official documentation](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/).
```
git clone git@github.com:normanjoyner/kubectl-tmux-ssh.git ~/.kube/plugins/kubectl-tmux-ssh
```

### Usage
```
 > kubectl plugin tmux-ssh --help
tmux-ssh allows users to SSH into Kubernetes nodes by opening a new pane for each matching node

Options:
  -i, --identity-file='': Selects a file from which the identity (private key) for public key authentication is read
  -l, --selector='': Selector (label query) to filter on, supports '=', '==', and '!='.(e.g. -l key1=value1,key2=value2)
  -p, --ssh-port='': SSH port
  -u, --ssh-username='': SSH Username

Usage:
  kubectl plugin tmux-ssh [flags] [options]

Use "kubectl options" for a list of global command-line options (applies to all commands).
```

### Examples
SSH into all nodes in the cluster:
```
kubectl plugin tmux-ssh
```

SSH into master nodes only:
```
kubectl plugin tmux-ssh -l node-role.kubernetes.io/master=""
```
