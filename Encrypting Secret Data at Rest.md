There is a documentation on kubernetes about encrypting data at rest: https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/

It's important to install `etcdctl` first, which is a command line tool for interacting with the etcd server. 

Afterwards we have to check if "**encryption-provider-config**" is installed on the [[kube-apiserver]].

```bash
ps -aux | grep kube-api | grep encryption-provider-config
```

or

```bash
ls /etc/kubernenets/manifests/
cat /etc/kubernenets/manifests/kube-apiserver.yaml
```

To enable it we need to create a configuration of kind **EncryptionConfiguration** and pass `encryption-provider-config` as an option.

```yaml
apiVersion: apiserver.config.k8s.io/v1
kind: EncryptionConfiguration
resources:
  - resources:
      - secrets
    providers:
      - identity: {}
      - aesgcm:
	      keys:
		    - name: key1
		      secret: SOME_SECRET
		    - name: key2
		      secret: SOME_SECRET
.
.
.
.
.
```

> There is a list of providers on the documentation page and their types of encryption.

> The order of the providers matter. The **identity** has no encryption, so if we want to encrypt secrets, we need to move the **identy** provider further below.

> Under `resources` section you can encrypt not only [[Secrets]] but also other configurations like [[Config Map]]

Once the configuration is created and saved, we need to change to [[kube-apiserver]] yaml to accept the encryptiopn configuration as per documentation.