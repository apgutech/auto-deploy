# Инструкция по работе с плейбуком

### Для развертывания стенда используется следующие параметры запуска:
#### Для развертывания кластера nginx необходимо запустить:
```
ansible-playbook -i inventory.yaml playbook.yaml -t depl-nginx
```
#### Для развертывания backend серверов необходимо запустить:
```
ansible-playbook -i inventory.yaml playbook.yaml -t depl-backend
```
#### Для развертывания всей инфраструктуры необходимо запустить:
```
ansible-playbook -i inventory.yaml playbook.yaml -t depl-all
```
### Для создания или восстановления используются следующие методы:
#### Для автоматической настройки mysql, репликации и создания БД, необходимо запустить:
```
ansible-playbook -i inventory.yaml playbook.yaml -t db_conf
```
>В данной лабе автоматически создастся ДБ test_db и далее резервные копии и восстановление будут связаны с этой ДБ.  
#### Для восстановления таблицы или несколько таблиц, необходимо запустить:
```
ansible-playbook -i inventory.yaml playbook.yaml -t table_recover -e "backup_name=<название бекапа на tftp сервере>"
или
ansible-playbook -i inventory.yaml playbook.yaml -t table_recover -e "backup_name=[<название1>,<название2> ... ]"
```
>В данном случае ansible playbook загрузит бекап(или несколько) с удалённого сервера (в данной лабе рассматривается tftp из за его простоты), далее распаковывает и восстанавливает потаблично. 
