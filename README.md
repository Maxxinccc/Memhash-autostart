1. Установка зависимостей

--Убедитесь, что у вас установлен Python версии 3.8 или выше.

Установите необходимые библиотеки:

pip install pyautogui pytesseract pillow python-dotenv

2. Установка и настройка Tesseract OCR

Скачайте и установите Tesseract OCR: https://github.com/tesseract-ocr/tesseract


После установки убедитесь, что путь к исполняемому файлу Tesseract добавлен в системные переменные PATH.
Если путь не добавлен автоматически, введите полный путь в скрипте:

pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'

3. Настройка файла .env

Заполните файл следующими параметрами:

X_COORD=951                       # X-координата кнопки 
Y_COORD=475                       # Y-координата кнопки 
ENERGY_AREA=750,176,61,25         # Координаты области для чтения энергии (x, y, (ширина, высота ,Это можно оставиь по умолчанию)) 
ENERGY_MIN=10000                  # Минимальная энергия для остановки майнинга 
ENERGY_MAX=20000                  # Максимальная энергия для запуска майнинга 
START_TIME=03:00                  # Время отложенного старта (UTC) 
ENERGY_CHECK_INTERVAL=1           # Интервал проверки энергии (оставляем по умолчанию) 
USE_START_TIME=True               # Использовать ли отложенный старт (True/False) 

4. Запуск программы

Убедитесь, что все зависимости установлены, а файл settings.env настроен.
Перейдите в папку со скриптом main.py.
Запустите скрипт командой:

python main.py

5. Настройка диапазона энергии

При первом запуске скрипт автоматически сохраняет скриншот области энергии в файл energy_area_<дата_время>.png.
Откройте этот файл и проверьте, корректно ли выбрана область.
Если область определена неверно, измените значение ENERGY_AREA в файле settings.env и перезапустите скрипт.

6. Отладка и логика работы

Отложенный старт:
Скрипт начнёт работу, если USE_START_TIME=True и текущее время UTC совпадает с указанным в START_TIME.
Если отложенный старт не требуется, установите USE_START_TIME=False.

Уровень энергии:
Если энергия меньше ENERGY_MIN, скрипт нажимает кнопку для остановки майнинга.
Если энергия больше ENERGY_MAX, скрипт нажимает кнопку для запуска майнинга.

7. Остановка программы
Чтобы остановить скрипт, нажмите Ctrl + C в командной строке.
