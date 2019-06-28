# Ralph On Rancher

[Ralph](https://github.com/allegro/ralph) is an open source CMDB/Asset management system.

Currently, there is a [manual procedure](ralph.yaml#2) that must be done after deploying workload in order to access the system.

This workload assumes you are using OpenStack Cinder as a storage backend for [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/).

Due to using OpenStack Cinder, `ReadWriteMany` is not allowed, meaning that containers can not share the same Persistent Volume. We use an `emptyDir` volume to share storage between containers.
