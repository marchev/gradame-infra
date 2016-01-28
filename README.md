# Grada.me Infra
**Grada.me Infra** е проект, който улеснява и автоматизира конфигурацията на инфраструктурата за проекта **Grada.me**. Това включва:
 - създаването на потребители и потребителски групи
 - инсталацията и конфигурирането на различни инструменти и услуги, които са необходими за проекта:
   - Build сървър
   - Хранилище за артефакти
   - Инструменти за анализ на кода

### Технологии
Технологиите, които се използват в проекта са:
 - [Ansible] - Безплатен софтуер за автоматизация и управление конфигурацията на сървъри.
 - [OpenSSH] - Пакет от инструменти, базирани на SSH протокола.

### Подготовка
1. Инсталирайте последната версия на `ansible` като следвате стъпките описани тук:    <http://docs.ansible.com/ansible/intro_installation.html>

2. *TODO: SSH конфигурация @ *`~/.ssh/config`

### Употреба
1. Клонирайте проекта **Grada.me Infra** от GitHub:
```sh
git clone https://github.com/marchev/gradame-infra.git
cd gradame-infra
```

2. Създайте файл с име `hosts` като копирате `hosts.template`:
```sh
cp hosts.template hosts
```

3. Редактирайте файла `hosts` като укажете hostnames на различните сървъри, които ще бъдат конфигурирани, в съответните секции. Например:
```
[build]
build.grada.me
```

4. За да се уверите, че всичко е правилно конфигурирано, изпълнете следната команда:
```sh
ansible all -i hosts -m ping
```
Резултатът трябва да бъде `SUCCESS`:
```json
build.grada.me | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

5. Изпълнете следната команда за автоматична конфигурация на сървърите:
```sh
ansible-playbook -i hosts playbook.yml
```

6. Voilà :smile:

[Ansible]: <http://ansible.com>
[OpenSSH]: <http://www.openssh.com>