# WITMOTION WT901BLECL
Здесь представлено небольшое web-приложение для использования датчика WT901BLECL (через USB и bluetooth) средствами react и TypeScript. Вся информация о датчике находится [тут](https://github.com/WITMOTION/WT901BLECL). Помимо этой документации, советую посмотреть документацию на используемый в датчике сенсор [WT901](https://images-na.ssl-images-amazon.com/images/I/B11fVGszLsS.pdf).

## 1 Состав ветки на react + TS
...

## 2 Запуск программы
Запуск программы осуществляется через npm. Приложение будет доступно в браузере по ссылке: http://127.0.0.1:3000/. 
```
npm start
```

Для подключения через Bluetooth проверьте, поддерживает/включен ли ваш браузер **Web Bluetooth API**. Вы можете воспользоваться следующими шагами:

1. Откройте новую вкладку в браузере.
2. В адресной строке введите "chrome://flags" (для Chrome) или "about:config" (для Firefox).
3. Ищите параметр "Web Bluetooth" и убедитесь, что он включен (заменить default/disable на enable).
4. Затем введите "chrome://bluetooth-internals" (для Chrome) или "about:bluetooth" (для Firefox).
5. Если вы видите раздел "Devices" и "Services", значит, ваш браузер поддерживает Web Bluetooth API.

Если вы используете другой браузер, Вы можете проверить список поддерживаемых браузеров на сайте Web Bluetooth Community Group.
 
## 3 Замечания

### 3.1 Документация
Если Вам необходимо изменить конфигурацию датчика, то советую сразу смотреть на документацию встроенного сенсора [WT901](https://images-na.ssl-images-amazon.com/images/I/B11fVGszLsS.pdf). В "родной" документации много чего не хватает.

### 3.2 Калибровка датчика

1. Калибровка акселерометра и гироскопа происходит в течение 3-х секунд после отправки команды (никаких сложностей, просто не трогайте его).
2. Калибровка магнитометра представляет из себя вращение датчика вокруг своих осей по 3 раза (см. [видео](https://youtu.be/smi2uePvC-Q?t=104))

### 3.3 Сложности

У данного датчика (по умолчанию) позиционирование происходит путём считывания данных с 9-ти степеней (по осям XYZ: 3 акселерометра, 3 гироскопа, 3 магнитометра). До калибровки магнитометра угол oZ всегда давал одно значение. После калибровки угол oZ работает адекватно ДО ЛЮБОГО резкого линейного толчка (~ 1g) датчика. Брак это или нет, мне не известно. Настоятельно советую забыть про магнитометр и СРАЗУ переключать датчик на 6 степеней.

## 4 Другая версия
Помимо этого, существует [репозиторий](https://github.com/LiDline/witmotion_WT901BLECL_py), где данное web-приложение реализовано на python и plotly dash.