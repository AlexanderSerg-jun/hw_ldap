1) Установка FreeIPA сервера
Как мы видим при использовании команды vagrant up у нас "развернулось 3 машины"
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/7e3a7692-a882-44a3-ac01-403b8363c809)

*Установим и настроим IPA-server. Подключимся к нему используя команду  ssh vagrant ipa.otus.lan
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/9366f9f4-ec08-48dc-ba6a-a0defc5d5e53)
1.1.Перейдем в пользователя root.Для этого используем команду sudo -i
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/f77ed69d-f12a-4587-a8ee-2f6837c60e9a)
1.2 Начнем установку IPA-Server
1.2.1 Используя команду timedatectl set-timezone Europe/Moscow, настроим часовой пояс
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/6b9f76c8-e360-4f6e-b5b3-0f9211f9964d)
1.2.2. Используя команду yum install -y chrony установим crony.После чего запустим данну утилиту и добавим ее в автозагрузку(для этого мы будем использовать команду yum install -y chrony && systemctl enable chronyd (данная команда означает, что после удачного выполнения первой команды ( установка утилиты) запускается вторая команда ( добавление в автозагрузку). Для этого мы используем &&)
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/ba137a97-7523-4fc3-a1bc-09e4de08a20b)



