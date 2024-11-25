# ESPHOME_SBER_SBDV-00123
Инструкция по прошивке розетки от Сбер девайсы SBDV-00123 в ESPHOME-LibreTiny. (Вы делаете это на свой страх и риск, я не несу ответственность за окирпиченные розетки)

Берем файл прошивки из данного репозитария. Это откомпилированная прошивка, правильно зашифрованная с подмененным загрузчикoм (OpenBK7231M_QIO_SBER_DEL.bin). Она прошьется в модуль сберрозетки, без ошибки контрольной суммы и позволит дальше шить розетку из EspHome-LibreTiny.

Основной инструмент - [https://github.com/openshwprojects/BK7231GUIFlashTool/releases/download/v1.1.0/bk7231flasher_1.1.0b.zip](https://github.com/openshwprojects/BK7231GUIFlashTool/releases/download/v1.3/bk7231flasher_1.3.3.zip) (утилита из проекта https://github.com/openshwprojects/BK7231GUIFlashTool )

Качаем, разархивируем, запускаем.

Предполагается, что розетка уже подключена к UART.

- В списке выбираем порт, который отождествлен с нашим UART.

- Нажимаем кнопочку "Open backups dir" и в открывшееся окно скачиваем прошивку [https://github.com/VMTestik/ESPHOME_SBER_SBDV-00123/OpenBK7231M_QIO_SBER_DEL.bin](https://github.com/VMTestik/ESPHOME_SBER_SBDV-00123/blob/main/OpenBK7231M_QIO_SBER_DEL.bin)

- Устанавливаем галочку "Show Advanced Options".  

- Устанавливаем галочку "Overwrite bootloader".

- В списке с устройствами выбираем BK7231M.

- В списке с прошивками выбираем скачанную стартовую прошивку - OpenBK7231M_QIO_SBER_DEL.bin.

- Нажимаем любую из кнопок (ниже "Set baud rate") (с бэкапом/без бекапа), какую именно, решать вам, может захотите сохранить сберовский бэкап и потом восстановить розетку в заводскую прошивку.

- При необходимости, замыкаем контакт CEN на землю или кратковременно передергиваем питание модуля

- Ждем окончания прошивки.

- Жмакаем кнопку "Restore RF part", со всем соглашаемся (это рандомизация MAC адреса, новая прошивка затрет бывший адрес). (ВОЗМОЖНО НЕ РАБОТАЕТ)

После этих операций вы можете прошить свою конфигурацию по UART или OTA, естественно, создав конфигурацию с использованием EspHome-LibreTiny. Прошитый модуль создает точку доступа SberFlasher с паролем 11111111. Можно подключиться к этой точке доступа, зайти на 192.168.4.1 и залить прошивку firmware.bin, созданную заранее. 
    
Конфиг брать из примера: [https://github.com/VMTestik/ESPHOME_SBER_SBDV-00123/device.yaml](https://github.com/VMTestik/ESPHOME_SBER_SBDV-00123/blob/main/device.yaml)

Хочу отметить, что тут я не описываю разборку розетки, подпайку к контактам и тд.

Для разборки розетки курим: https://mysku.club/blog/russia-stores/101393.html

Гайд основан на: https://github.com/Brokly/ESPHOME_SBER_SBDV-00115
