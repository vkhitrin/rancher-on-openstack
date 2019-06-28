# Ralph On Rancher

[Ralph](https://github.com/allegro/ralph) is an open source CMDB/Asset management system.

Currently, there is a [manual procedure](ralph.yaml#L2) that must be done after deploying workload in order to access the system.

This workload assumes you are using OpenStack Cinder as a storage backend for [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/).

Due to using OpenStack Cinder, `ReadWriteMany` is not allowed, meaning that containers can not share the same Persistent Volume. We use an `emptyDir` volume to share storage between containers.

## Resources Deployed

### Persistent Volumes
* ralph-dbdata - used by `ralph-db` container in order to store mysql database.

### Services
* ralph - used to access django app
* ralph-nginx - used to serve content to users
* ralph-db - used to access mysql database

### Config Mp
* ralph-nginx-conf - nginx configuration file