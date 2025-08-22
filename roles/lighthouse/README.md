lighthouse-role
=========

Роль выполняет:  
1. установку git и nginx для использования в качестве веб-сервера   
2. клонирование git-репозитория Lighthouse с исходным кодом  
3. создание конфигурационного файла nginx для доступа к статическим ресурсам Lighthouse  
4. запуск nginx  

Requirements
------------

1. Операциооная система на базе Debian
2. Предустановленная БД Clickhouse  


Role Variables
--------------
`vars/main.yml`:  
Содержит в параметрах ссылку на git-репозитория Lighthouse с исходным кодом и список пакетов, обязательных к установке для работы роли:     
```yaml
lighthouse_code_src: "https://github.com/VKCOM/lighthouse.git"
lighthouse_code_src_version: d701335
lighthouse_data_dir: "/usr/share/nginx/html/lighthouse/"
lighthouse_packages:
  - nginx
  - git

lighthouse_nginx_port: 8080
light


Example Playbook
----------------

Пример добавление роли в playbook:  
```yaml
- name: Install Lighthouse
  hosts: lighthouse
  gather_facts: false
  roles:
    - role: lighthouse-role
      tags: lighthouse
```

License
-------

BSD
