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
1.2.3 Используя " &&"  остановим и уберем firewalld из автозагрузки systemctl stop firewalld && systemctl disable firewalld

![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/89515d8c-31aa-4727-8ec9-d819bb256792)

*Что бы убедиться что команда сработала выведем состояние демона командой systemctl status firewalld. Как мы видим его статус inactive(dead).
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/59323382-6bea-4252-8bae-1beb5f66999e)
1.2.4.Остановим SElinux. Для этого воспользуемся командой setenforce 0
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/799085c5-9cdb-4d94-813d-3f78c9d979a6)
1.2.5. Изменим параметр Selinux на disabled vi /etc/selinux/config
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/794e0847-6a2d-45cc-9361-23d21a1cf910)
1.2.6 Для дальнейшей настройки FreeIPA нам потребуется, чтобы DNS-сервер хранил запись о нашем LDAP-сервере. В рамках данной лабораторной работы мы не будем настраивать отдельный DNS-сервер и просто добавим запись в файл /etc/hosts
vi /etc/hosts
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/c200f765-7915-47f4-832a-232900e557b0)
1.2.7.Установим модуль DL1: yum install -y @idm:DL1 и активируем модуль dnf module enable idm:DL1

![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/19e94050-02cc-43f2-9e6a-2171398a7432)
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/a9daefe3-4767-4bbf-98fc-a1afa8bb0c6e)

1.2.8. Установим FreeIPA-сервер: dnf install -y freeipa-server
![изображение](https://github.com/AlexanderSerg-jun/hw_ldap/assets/85576634/1d227c31-2a38-452a-a0ac-93f01b8764c1)




