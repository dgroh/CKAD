Labels & Selectors are a standard method to group things together.

Labels are properties attached to its type, for example:

```yaml
Class: Mammal
Kind: Domestic
Color: Green
```

Selectors help us filter those items, for example, by querying Mammals we can select `Class=Mammal` which would retrieve all animals of type **Mammal**. 

## Labels

Labels can be defined in the [[POD]] definition file unter the section **metadata** named **labels**.

### Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - name: nginx-container
      image: nginx
```

For the example above we have a Pod which represents an **app of type front-end**.

## Selector

Once a label has been defined, it's possible to query the resource by its label using the selector option.

### Example

`kubectl get pods --selector app=App1`

