## Установка ЛКС
sudo apt update

apt-get install lxc debootstrap bridge-utils lxc-templates

apt-get install lxd-installer

lxd init(Здесь просто нажимаем на Enter что уствновились значения по умолчанию)

Проверяем

lxc storage list

![установка лкс](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/HomeWork2_scrin1.jpg)
## Cоздаем контейнер

sudo apt update

lxc-create -n test123 -t ubuntu --создаем контейнер

sudo lxc-ls -f проверить какие контейнеры есть

lxc-start -n test123 -- запускаем

lxc-attach -n teat123 -- войдем в него

free -m —проверяем пямаять

exit -- выходим

lxc-stop -n test123 - -закрываем

![создаем контейнер](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/HomeWork2_scrin2.jpg)

nano /var/lib/lxc/test123/config-открываем

## Ограничиваем контейнер 256 Мб ОЗУ 

lxc.rootfs.path = dir:/var/lib/lxc/test1234/rootfs — путь

lxc.uts.name = test1234 -- имя

Network configuration — Конфегурация сети

lxc.cgroup2.memory.max = 256M -- ограничиваем(В режиме Вставка делаем запись)

lxc-start -n test123 -- запускаем

lxc-attach -n teat123 -- войдем в него

free -m -- проверяем пямаять

!!!Видим что наше ограничение работает!!!
