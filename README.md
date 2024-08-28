# AmneziaWG kernel module build tool for OpenWrt devices
Description only in russian
## Что делает?
Собирает пакеты AmneziaWG для последней snapshot версии Openwrt
### Как настроить?
В форке нужно настроить Actions workflow main.yml (.github/workflows/build-module.yml) на билд модуля под свой девайс, 
указав три параметра в секции *jobs.build.strategy.matrix.build_env*
- target: таргет устройства для сборки модуля
- subtarget: сабтаргет устройства для сборки модуля

Target и subtarget можно взять со страницы загрузки устройств <https://firmware-selector.openwrt.org>, в найденном устройстве в секции __About this build__:\
``
Platform mediatek/filogic
``\
здесь target -- mediatek, subtarget -- filogic.\
Итого, в build-module.yml секция *jobs.build.strategy.matrix.build_env* должна выглядеть следующим образом:
```yml
jobs:
  build:
    name: "v${{ matrix.build_env.tag }} - ${{ matrix.build_env.pkgarch}} :: ${{ matrix.build_env.target}}/${{ matrix.build_env.subtarget}} build"
    runs-on: ubuntu-latest
    strategy:
      matrix:
        build_env:
            target: mediatek
            subtarget: filogic
```
### Как собрать
Вручную запустить workflow и ждать успешной сборки

После удачной сборки в проекте появится релиз с тремя пакетами: модуль ядра, тул и плагин для luci. Их нужно поставить из интерфейча luci. Далее перегрузить устройство.
Настройки awg появятся в разделе *Network/Interfaces/Add new interface*
