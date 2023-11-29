# Automated Redpill Loader (i18n)

Библиотека arpl i18n (многоязычная оптимизированная версия):

### Оригинальная версия:
<b>https://github.com/fbelavenuto/arpl</b>
* [En](./arpl-README-En.md)
* [Zh](./arpl-README-Zh.md)

### Китайский язык:
<b>https://github.com/wjz304/arpl-zh_CN</b>
* Синхронизируется только китайская оригинальная версия, поэтому функции остаются в соответствии с исходной версией.

### i18n: 
<b>https://github.com/wjz304/arpl-i18n</b>
* Многоязычная поддержка.
* Содержит мои модификации.


## проиллюстрировать
* ### [Демонстрация метода ввода команд](https://www.bilibili.com/video/BV1T84y1P7Kq) https://www.bilibili.com/video/BV1T84y1P7Kq
* Переключение между версиями arpl (обновление меню, приращение):
     ```shell
     # Введите следующую команду в оболочке, чтобы изменить и обновить репозиторий.
     # Если вы хотите переключиться на исходную версию, измените BikerIndian/arpl-i18n во второй команде на fbelavenuto/arpl
     # Если вы переключитесь на китайскую версию, измените BikerIndian/arpl-i18n во второй команде на wjz304/arpl-zh_CN
    CURREPO=`grep "github.com.*update" menu.sh | sed -r 's/.*com\/(.*)\/releases.*/\1/'`
    sed -i "s|${CURREPO}|wjz304/arpl-i18n|g; s|ACTUALVERSION=\"v\${ARPL_VERSION}\"|ACTUALVERSION=\"v0.0\"|g" /opt/arpl/menu.sh
    # Войдите в меню настроек, чтобы выполнить операцию обновления arpl.
    # Пожалуйста, перезагрузите компьютер после обновления.
    ```
* Переключение между версиями arpl (ручной режим, полная версия):
 ```shell
 # Загрузите необходимую версию под оболочкой или вручную загрузите ее в /opt/arpl/
 curl -kL https://github.com/fbelavenuto/arpl/releases/download/v1.1-beta2a/arpl-1.1-beta2a.img.zip -o /opt/arpl/arpl.zip
 # Распаковать
 unzip /opt/arpl/arpl.zip
 # монтируем img
 losetup /dev/loop0 /opt/arpl/arpl.img
 # Копируем раздел p1 p3
 mkdir -p /mnt/loop0p1; mount /dev/loop0p1 /mnt/loop0p1; cp -r /mnt/loop0p1/* /mnt/p1/; umount /mnt/loop0p1
 mkdir -p /mnt/loop0p3; mount /dev/loop0p3 /mnt/loop0p2; cp -r /mnt/loop0p3/* /mnt/p3/; umount /mnt/loop0p3
 # Удалить img
 losetup -d /dev/loop0
 # Если установленная версия не содержит DSM, который вы устанавливаете в данный момент, попробуйте удалить его. /mnt/p1/user-config.yml, /mnt/p3/*-dsm, /mnt/p2/*
 rm -rf /mnt/p1/user-config.yml /mnt/p3/*-dsm /mnt/p2/*
 # Перезапуск
 reboot
 ```


## переводить
```shell
sudo apt install gettext
git clone https://github.com/wjz304/arpl-i18n.git
cd arpl-i18n/files/board/arpl/overlayfs/opt/arpl
xgettext -L Shell --keyword=TEXT *.sh -o lang/arpl.pot
sed -i 's/charset=CHARSET/charset=UTF-8/' lang/arpl.pot    # The above process has been completed.
msginit -i lang/arpl.pot -l zh_CN.UTF-8 -o lang/zh_CN.po    # Replace the language you need.
# translate the lang/zh_CN.po.
msgfmt lang/zh_CN.po -o lang/zh_CN.mo    # This process will be automatically processed during packaging.
```

## поблагодарим товарища wjz304 ))
<img src="https://raw.githubusercontent.com/wjz304/wjz304/master/my/20220908134226.jpg" width="400">



