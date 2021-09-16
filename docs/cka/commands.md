# Commands

Set Aliases 

```
alias k="kubectl"
```

#### Find namespace and write to a file


```
(k get ns | awk '{print $1}') > namespaces.txt
```

#### Find a specific pod namespace and write/append to a file

First find the namespace

```
k get po -A| grep kube-schedule*
kube-system   kube-scheduler-master
```

Then use `awk` to print the column.

```
((k get po -A| grep kube-schedule*) | awk '{print $1}') >> namespaces.txt
```

Print contents of the file

```
$cat namespaces.txt
NAME
default
dev
kube-node-lease
kube-public
kube-system
kube-system
```
