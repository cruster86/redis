# ansible-redis-sentinel

Ansible Playbook to deploy a High Availability Redis with Sentinel

## Getting started

1. Create 3 servers with public-key authentication
2. Edit `inventory.ini` file and set `ansible_host=` with the corresponding IP address for each redis server.
3. Run playbook `setup-redis-sentinel.yml`

    ```bash
    ansible-playbook setup-redis-sentinel.yml -i inventory.ini
    ```

## Notice

1. The configuration for Redis and Sentinel are defined in `redis.conf.j2` and `sentinel.conf.j2`. The playbook explicitly uses `:` to separate each line and use `regexp` to update the corresponding file on the server. Therefore, the playbook will only touch the necessary setting and doesn't modify any other default settings.
2. Make sure that the `role` in `inventory` is correct before running the playbook. For example, if the Sentinel changes the master to a replica. You need to change the `role` to match the current master-replica setup. Otherwise, the playbook will mess up the setting of Sentinel.

---
https://github.com/quanhua92/ansible-redis-sentinel
