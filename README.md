# AmneziaWG kernel module build tool for OpenWrt devices
Description only in russian
## Что делает
Собирает пакеты AmneziaWG для выбранной release либо последней доступной snapshot версии Openwrt
## Как собрать
- Сделать форк репозитория
- Перейти в actions
- Запустить workflow для сборки пакетов c параметрами для вашего девайса
```
branch: release/snapshot
version: 25.05.5 - (только для release)
target: mediatek
subtarget: filogic
```
- Ждать успешной сборки, она появится во разделе релизов со следующими собранными пакетами: модуль ядра, тул и плагин для luci