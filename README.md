# Реализация Windows Precision Touchpad для Apple MacBook и Magic Trackpad 2

[![Build Status](https://ligstd.visualstudio.com/_apis/public/build/definitions/7694e0d0-94e3-4fd2-b39a-ecd261e1ba2e/22/badge)](https://ligstd.visualstudio.com/Apple%20PTP%20Trackpad/_build?definitionId=22)

Этот проект реализует Windows Precision Touchpad Protocol для семейства Apple MacBook и Magic Trackpad 2 в среде Windows 10. Поддерживаются как USB (традиционные и T2), так и SPI и Bluetooth-трекпады.

## Официальный драйвер?

Bootcamp 6.1.5 предлагает официальный драйвер для моделей на базе T2 и Magic Trackpad 2. Если у вас такой Mac, можно рассмотреть использование официального драйвера. Однако для старых моделей (например, MacBook до 2018/2019 годов) это единственная реализация (пока).

## Видео-демонстрация (YouTube)

[![Смотреть видео](https://img.youtube.com/vi/-GWlfw7omdo/hqdefault.jpg)](https://youtu.be/-GWlfw7omdo)

## Руководство по установке

**ВАЖНО:** Из-за изменений в политике Microsoft по подписанию драйверов и требований к сертификатам EV, CI-сборки после 06.01.2021 не подписываются автоматически. Они поддерживаются через TestSigning, но не рекомендуются для обычных пользователей. Корректно подписанные пакеты WHQL и EV будут выпускаться вручную и доступны на странице релизов.

0. Полностью удалите `Trackpad++`, если он был установлен ранее.
1. Перейдите в раздел релизов на GitHub и скачайте последнюю версию для вашей архитектуры.
2. Щелкните правой кнопкой по `AmtPtpDevice.inf` и выберите "Установить".
3. Если у вас Magic Trackpad 2, и вы хотите использовать его по Bluetooth, вручную выполните сопряжение в настройках ПК.

**Примечание:** Не требуется включать test signing или устанавливать сертификат вручную. Это может вызвать проблемы при установке. Подробнее [здесь](https://github.com/imbushuo/mac-precision-touchpad/issues/228#issuecomment-538689587).

## Удаление драйвера (важно для переустановки `Trackpad++` и аналогичных программ)

Дополнительные сведения [здесь](https://magicutilities.net/magic-trackpad/help/mac-precision-touchpad-driver-installed).

1. Откройте Диспетчер устройств.
2. Найдите "Apple Precision Touch Device", "Apple Multi-touch Trackpad HID filter" и "Apple Multi-touch Auxiliary Services".
3. Щелкните правой кнопкой, выберите "Удалить устройство" и отметьте "Удалить драйвер".
4. Обновите список устройств.

## Установка через Chocolatey

Драйвер доступен как [Chocolatey-пакет](https://chocolatey.org/packages/mac-precision-touchpad/). Установить можно командой:

```
choco install mac-precision-touchpad
```

## Для разработчиков

- Версия SPI/T2 — драйвер в режиме ядра, использует KMDF Framework v1.23. Bluetooth-драйвер использует KMDF Framework 1.15. Требуется Windows 10 Driver Development Kit версии 2004 или выше.
- USB-версия — драйвер пользовательского режима, использует UMDF Framework v2.15. Требуется Windows 10 Driver Development Kit версии 2004 или выше.
- Конфигурация `ReleaseSigned` зарезервирована для продакшн-сборки. Если вы попытаетесь собрать с этим параметром, драйвер будет неподписанным (из-за требований EV-сертификата).

**[Автор проекта](https://github.com/imbushuo/mac-precision-touchpad)**

## Лицензия

- USB-драйвер лицензирован под [GPLv2](LICENSE-GPL.md).
- SPI-драйвер лицензирован под [MIT](LICENSE-MIT.md).


