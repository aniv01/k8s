#### K8s Volumes
----
- Persistent Volume Claim (Request For Storage)
  - Piece of pre-provisioned storage inside the k8s cluster
  - Claims must me in same namespace where the POD exists.
- Persistent Volume (Piece of Storage in the cluster)
  - Storage request by a user (developer)
  - Persistent Volumes are not namespaced, they are accessible to the whole cluster.
- Life Cycle Of Persistent Volume
  - Provisioning
    - Cluster administrator creates the storage volume. These can be any storage type such as NFS, Block etc..
    - They can be provisioned on 2 ways
      - Static
      - Dynamic
  - Binding
    - We bind the storage request (PVC) with the persistent volume
    - As soon as the PVC is created, the control loop in the master will watches for any new PVC requests and binds the matching PV if it is available under the requested pool
  - Reclaiming
    - Recycled
    - Retained
    - Deleted
#### K8s Volumes Provisioning
---
- Static
  - PV needs to be created before PVC
- Dynamic
  - PV is created at the same time of PVC
  - In case of dynamic PVC's, when the developer doesn't mention the storage class under PVC config a default storage class will be applied.
#### Local vs Remote Volume Types
- Each volume type has its own usecase.
- Local volume type violates the below data persistent rules.
  - Being tied to 1 specific node
  - Surviving cluster crashes
Note: For DB persistence, always use the remote volume types.

