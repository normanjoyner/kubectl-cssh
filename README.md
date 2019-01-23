# kubectl-cssh

## About

### Description
A kubectl plugin to SSH into Kubernetes nodes within separate tmux panes

### Prerequisites
In its current form, `kubectl-cssh` requires [tmux](https://github.com/tmux/tmux) to be installed and running to work properly. We are [considering alternative fallback functionality](https://github.com/containership/kubectl-cssh/issues/20) to support users without `tmux`.

### Installation
The preferred way to install `kubectl-cssh` is through [krew](https://github.com/GoogleContainerTools/krew). After following the [installation documentation](https://github.com/GoogleContainerTools/krew#installation), you can install `kubectl-cssh`.
```
kubectl krew install cssh
```

If you'd like to install the plugin manually, simply add `kubectl-cssh` to your `$PATH`. For more information about how plugins are loaded, please see the [official documentation](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/).
```
git clone git@github.com:containership/kubectl-cssh.git ~/.kube/plugins/kubectl-cssh
```

### Usage
```
 > kubectl cssh --help
Allows users to SSH into Kubernetes nodes by opening a new tmux pane for each matching node

Options:
  -a, --address-type='ExternalIP': Node address type to query for (e.g. InternalIP/ExternalIP)
  -i, --identity-file='': Selects a file from which the identity (private key) for public key authentication is read
  -l, --selector='': Selector (label query) to filter on, supports '=', '==', and '!='.(e.g. -l key1=value1,key2=value2)
  -p, --port='': SSH port
  -u, --username='': SSH Username

Usage:
  kubectl cssh [flags] [options]
```

### Examples
SSH into all nodes in the cluster:
```
kubectl cssh
```

SSH into master nodes only:
```
kubectl cssh -l node-role.kubernetes.io/master=""
```

SSH into master nodes in private network topologies:
```
kubectl cssh -l "kubernetes.io/role=master" -a "InternalIP"
```

## Contributing
Thank you for your interest in this project and for your interest in contributing! Feel free to open issues for feature requests, bugs, or even just questions - we love feedback and want to hear from you.

Pull requests are also always welcome! However, if the feature you're considering adding is fairly large in scope, please consider opening an issue for discussion first.
See [CONTRIBUTING.md](/CONTRIBUTING.md) for more details.
