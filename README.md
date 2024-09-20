# OTUS PRO Homework 02-Vargant

### Домашняя работа 02: Обновление ядра Debian 12 через Ansible

### Вариант1: Если Ansible уже развернут:

### 1) Зайдите на OS, где установлен Ansible с root доступом
   - Примечание: используйте пользователя **root** либо команды: **su - root** либо **sudo -i**

### 2) Выполните данную команду на удаленной машине (где развернут Ansible):
```
apt update -y && apt install git -y ; git clone https://github.com/avlikh/Otus_pro_02.git /ansible;
```
### 3) Внесите изменения в файл: /ansible/hosts (измените ip-адрес хоста testdeb1 на актуальный)

### 4) Выполните данную команду на удаленной машине, что бы запустить обновление ядра:
```
export ANSIBLE_CONFIG=/ansible/ansible.cfg && cd /ansible/ && ansible-playbook /ansible/playbooks/playbook_update_debian12_kernel.yml -u root --ask-pass;
```
### 5) Вам потребуется ввести пароль пользователя root для выполнения обновления ядра на удаленной машине (я не использовал rsa-ключи) 
   - Примечание: В процессе обновления ядра, сервер будет 1 раз перезагружен.

### Вариант2: Если Ansible не развернут:

### 1) Зайдите на OS, где будет развернут Ansible с root доступом
   - Примечание: используйте пользователя **root** либо команды: **su - root** либо **sudo -i**
### 2) Выполните данную команду на удаленной машине (где будет развернут Ansible):
```
apt update -y && apt install git -y ; git clone https://github.com/avlikh/Otus_pro_02.git /ansible; /ansible/install_andible_and_lesson2.ssh
```
   - Примечание: Будет выполнена установка репозиториев, основных пакетов и утилит, Ansible и запущен playbook по обнавлению ядра Debian 12 на хосте testdeb1 с ip-адресом:10.68.7.11

### 3) Вам потребуется ввести пароль пользователя root для выполнения обновления ядра на удаленной машине (я не использовал rsa-ключи)
   - Примечание: В процессе обновления ядра, сервер будет 1 раз перезагружен.
-------------------------------------------------------------------------------------------------------------------------------------------- 
### Что делает Playbook Ansible:

### 1) копирует на удаленную машину файл со стандартными репозиториями
### 2) Выводит версию текущего ядра
### 3) Обновляет кэш пакетов
### 4) Обновляет пакеты в системе
### 5) Устанавливает последнюю версию ядра из стандартного репозитория Debian
### 6) Перезапускает систему для обновления ядра
### 7) Ждет 10 секунд и проверяет доступность системы. Повторяет проверки в течении 5 минут
### 8) Показывает версию старого и нового ядра



