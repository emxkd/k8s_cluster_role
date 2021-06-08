# k8s_cluster_role
k8s master and worker cluster over aws using ansible roles

# How to use the role:

This repository focuses on configuring k8s cluster (1 master and 2 slave nodes) over AWS. 

If you already have precreated AWS instances than you can simply put their IPs in _ip.txt_ file and execute _final.yml_ playbook using the command:

```
ansible-playbook final.yml
```
But if you do not have AWS pre-created instances then I've created another playbook which will not only launch master and slave nodes but also update their IPs dynamically in inventory file (_ip.txt_) and then configure k8s cluster on it.

So for this you need to follow these steps:

1. In vars.yml fill all the AWS instance related details which are required to launch the instances.

2. In the same directory (i.e., k8s_cluster_role), make ansible-vault to store the AWS IAM user access_keyand secret_key. Create file with the name ```credentials.yml``` only, because it is hard-coded in the program using the command:

```
ansible-vault create credentials.yml
```

And inside this file input AWS access_key and secret_key in the following format:

```
access_key: <access_key>
secret_key: <secret_key>
```

First playbook will create instances in AWS and we can run the playbook using the command:

```
ansible-playbook --ask-vault-pass ec2_create.yml
```

And next, you need to run the playbook _final.yml_ using the command:

```
ansible-playbook final.yml
```

That's all folks... Thankyou for reading :)

I would also like to thank Prithviraj Singh for his help and guidance throughout this project ^_^
