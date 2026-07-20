## Как devops c нуля развернул мониторинг?

### 1. создал 2 сервера (один test_project - имитация реального проекта, другой monitoring_server)

### 2. узнал ip двух серваков.

### 2.1 вставил ip в ansible/inventory/group_vars/all/main.yml  >    MONITORING_SERVER_IP: "93.77.186.158"

### 3. задал переменные окружения + прописал пароль внутрь password_file.txt

```
export WORK_DIR=/root/dir
export ANSIBLE_CONFIG=/root/dir/ansible/ansible.cfg
export ANSIBLE_VAULT_PASSWORD_FILE=/root/dir/password_file.txt
```

### 4. создал логин/пароль для grafana + прописал зашифрованные значения внутрь ansible/inventory/group_vars/all/main.yml

```
ansible-vault encrypt_string 'its-admin' --name 'GRAFANA_ADMIN_USER'
ansible-vault encrypt_string 'gwrgwrg' --name 'GRAFANA_ADMIN_PASSWORD'
```

### 5. создал папку тестового проекта и заполнил по шаблону(ip, project_name, password, ssh-key)


### Запуск MONITORING_SERVER
```
ansible-playbook monitoring/projects/monitoring_server/playbook.yml --inventory=monitoring/projects/monitoring_server/inventory.yml -vv --inventory=ansible/inventory/
```


### Запуск MONITORING_CLIENT (тестовый проект [test])
```
ansible-playbook monitoring/projects/test/playbook.yml --inventory=monitoring/projects/test/inventory.yml -vv --inventory=ansible/inventory/
```
