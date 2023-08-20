# ConteinL2
1) Устанавиваем lxc контейнер с компонентами 
   apt-get install lxc debootstrap bridge-utils lxc-templates
   apt-get install lxd-installer
   lxd init(Enter - значения по умолчанию)
2) Проверяем (выводится табличка)
   lxc storage list
4) Создаем контейнер
   lxc-create -n test01 -t ubuntu -f /usr/share/doc/lxc/example/lxc-veth.conf
5) Запускаем контейнер
  lxc-start -n test01
6) Входим в контейнер (изменится имя аккаунта на #)
  lxc-attach -n test01
7) Проверяем что контейнер изолирован ip a (видим только лупбак интерфейс - мы изолированы)
   ip a
8) Проверяем выделенную память контейнеру (значение по умолчанию)
   free -m
9) Выъодим из контейнера
   exit
10) Закрываем контейнер
  lxc-stop -n test01
11) Открываем в редакторе файл контейнера (редактируем Network configuration - ограничиваем выделяемый объем памяти) и записываем
    nano /var/lib/lxc/test123/config
    
    Network configuration
      lxc.cgroup2.memory.max = 256M 
13) Повторяем последовательно шаги 5,6,8 (память ограничена 256Мб)
![L2_1](https://github.com/PavelE13/ConteinL2/assets/94640966/fc6efc4d-11ee-4b07-a25d-300f04ec0576)
![L2_2](https://github.com/PavelE13/ConteinL2/assets/94640966/484f1966-110a-436b-9135-12b10bfa74cc)
