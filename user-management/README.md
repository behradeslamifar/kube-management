# Create Namespace and User in Kubernetes
## Usage 
Install dependencies first. You have to use VPN or Proxy because of sanction.
```
ansible-galaxy  install -r requirements.yml
```

Choose access level based on this table:  

| Role          | Description   |
|:------------- |:--------------|
| developer     | `edit` access. edit access do permite modify role and rolebinding only |
| teamlead      | `admin` access. admin access all thing include role and rolebinding in namespace|
| cluster_view  | `view` access. view access all object exclude secrets cluster wide  |
| cluster_admin | `cluster_admin` access. It's a God |


Add user or namespace to inventory(hosts.yml)  
```
all:
  hosts:
    localhost:
      ansible_connection: local
     users:
       - user: b-eslamifar
         role: cluster_view
         namespaces: []
       - user: a-ahmadi
         role: developer
         namespace:
           - ns-test
           - ns2-test

     namespaces:
       - name: ns-test
         quota:
           request_ephemeral_storage: "1Gi"
           limit_ephemeral_storage: "2Gi"
           loadbalancer_limit: "0"
       - name: ns2-test
         quota:
           request_ephemeral_storage: "1Gi"
           limit_ephemeral_storage: "2Gi"
           loadbalancer_limit: "0"
```
