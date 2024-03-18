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
Имена указывать без .gz 
```
ansible-playbook -i inventory.yaml playbook.yaml -t table_recover -e '{"backup_name": [<backup1>]}
```
>В случае с восстановлением одной таблицы
или
```
ansible-playbook -i inventory.yaml playbook.yaml -t table_recover -e '{"backup_name": [<backup1>,<backup2>, ...]}'
```
>В случае с восстановлением нескольких таблиц

>В данном случае ansible playbook загрузит бекап(или несколько) с удалённого сервера (в нашем случае с помощью протокола scp), далее распаковывает и восстанавливает потаблично. 


