# Implment Process

## Working flow and process
 - We are applying taint "dhruv=true" to each node so every pod have must have tolration with this taint.
 - We are create one deployment with tolration "spot:true" that is diffrent fromtaint so our deploymnet pod is not schdule anywhere and our karpenter create one spot instance based on2 nodepool and ec2nodeclass file.

## Apply taint to node
```sh
kubectl taint node-name key=value:effect
```
- ie. kubectl taint nodes ip-172-31-24-219.ap-south-1.compute.internal  dhruv=true:NoSchedule

## Remove taint to node
```sh
kubectl taint node-name key=value:effect- 
```
-- ie. kubectl taint nodes ip-172-31-24-219.ap-south-1.compute.internal  dhruv=true:NoSchedule- 

## Add tolration to pod
- add tolration block look like,

```yaml
tolerations:
  - key: "spot"
    operator: "Equal"
    value: "true"
    effect: "NoSchedule"


