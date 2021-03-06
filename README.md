Tomizawa FZ-880B soldering station controller open-source firmware
==================================================================

Цель данного проекта - реанимация умершего чуда китайской инженерной мысли: паяльника с терморегуляцией Tomizawa FZ-880 и его клонов.
Т.к. схемотехника агрегата мягко говоря не очень, возможно еще кому-то пригодится...

Итак, самое слабое место - схема питания МК. Если паяльник перестал подавать признаки жизни и при включении в розетку монотонно горят один илн несколько светодиодов - ваш случай.

Для восстановления потребуется:
1. Прокачать до второго уровня или выше схему питания микроконтроллера (см.фото).
2. Изготовить методом лута печатку под новый МК STM8S003F3P6, прикупив последний где-нибудь тут: http://www.ebay.com/sch/i.html?&_nkw=stm8s003f3
3. Прошить МК и установить плату вместо стокового контроллера на свободное место.

Файлы:
1. firmware_vX.X.hex - сама прошивка.
2. ctrl-brd_reduced-F_Cu.ps - шаблон для изготовления платы (формат post-script).
3. Все остальное - если будете заморачиваться с допилкой под сови нужды и повторной сборкой.

Для компиляции использовался sdcc 3.4.3 #9179 под linux (ubuntu 14.04).
Для шитья - Versaloon (в проекте) или более доступное средство: ST_Link V2.

Features:
1. Термостабилизация ПИД-регулятором. Точность 5-10С.
2. Предварительный прогрев до температуры режима n+1 для сокращения времени нагрева жала.
3. Индикация выхода на рабочий температурный режим миганием светодиода.
4. Отключение паяла длинным нажатием.

TODO (если будет не лень):
1. Режим калибровки: точная подстройка температуры с сохранением в eeprom.
