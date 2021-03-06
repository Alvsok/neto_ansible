# Самоконтроль выполненения задания

1. Где расположен файл с `some_fact` из второго пункта задания?
>https://github.com/Alvsok/neto_ansible/blob/main/playbook/group_vars/all/examp.yml#L2
2. Какая команда нужна для запуска вашего `playbook` на окружении `test.yml`?
>$ ansible-playbook site.yml -i inventory/test.yml
3. Какой командой можно зашифровать файл?
>$ ansible-vault encrypt group_vars/deb/examp.yml
4. Какой командой можно расшифровать файл?
> $ ansible-vault decrypt group_vars/deb/examp.yml
5. Можно ли посмотреть содержимое зашифрованного файла без команды расшифровки файла? Если можно, то как?
> $ ansible-vault view group_vars/deb/examp.yml
6. Как выглядит команда запуска `playbook`, если переменные зашифрованы?
>$ ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass
7. Как называется модуль подключения к host на windows?
> ```ansible_connection: winrm```
8. Приведите полный текст команды для поиска информации в документации ansible для модуля подключений ssh
> Не знаю... Я бы искал где-то здесь:    
> $ ansible  --help    
> или тут:    
> https://docs.ansible.com/ansible/latest/index.html
9. Какой параметр из модуля подключения `ssh` необходим для того, чтобы определить пользователя, под которым необходимо совершать подключение?> 
> ```ansible_user=myuser```     



1. Попробуйте запустить playbook на окружении из `test.yml`, зафиксируйте какое значение имеет факт `some_fact` для указанного хоста при выполнении playbook'a.

> ![playbook1](./Scr11-31-41.png)




2. Найдите файл с переменными (group_vars) в котором задаётся найденное в первом пункте значение и поменяйте его на 'all default fact'.
> ![playbook2](./11-59-18.png)

3. Воспользуйтесь подготовленным (используется `docker`) или создайте собственное окружение для проведения дальнейших испытаний.
4. Проведите запуск playbook на окружении из `prod.yml`. Зафиксируйте полученные значения `some_fact` для каждого из `managed host`.
> ![playbook4](./20-24-49.png)
5. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились следующие значения: для `deb` - 'deb default fact', для `el` - 'el default fact'.
6.  Повторите запуск playbook на окружении `prod.yml`. Убедитесь, что выдаются корректные значения для всех хостов.
> ![playbook4](./20-33-32.png)
7. При помощи `ansible-vault` зашифруйте факты в `group_vars/deb` и `group_vars/el` с паролем `netology`.
8. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь в работоспособности.
> ![playbook4](./20-40-13.png)
9. Посмотрите при помощи `ansible-doc` список плагинов для подключения. Выберите подходящий для работы на `control node`.
> Не вполне понял. Доступные плагины:     
```ansible-doc -t connection -l```
![playbook4](./20-54-29.png)
Но что с этим делать непонятно…

10. В `prod.yml` добавьте новую группу хостов с именем  `local`, в ней разместите localhost с необходимым типом подключения.
11. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь что факты `some_fact` для каждого из хостов определены из верных `group_vars`.
![playbook4](./21-01-42.png)