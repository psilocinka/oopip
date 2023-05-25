# не сдана 6 и 7

условия:
Часть 1
Программу, разработанную в лабораторной работе No 6, преобразовать
следующим образом: для обеспечения движения геометрических фигур в окне
вместо таймера использовать потоки. Для каждой геометрической фигуры
использовать свой поток. Потоковая функция должна быть одна, объект
«Фигура» передается в потоковую функцию через параметр (для передачи
дополнительных данных в потоковую функцию в качестве параметра можно
задать указатель на структуру). При необходимости использовать
синхронизацию.
Часть 2
Необходимо обеспечить синхронизацию двух приложений.
Первое приложение. Приложение с потоками преобразовать так, чтобы
движение фигур в потоках начиналось не сразу, а после получения сигнала от
второго приложения. При получения сигнала потоки начинают работать до тех
пор, пока от второго приложения не придет другой сигнал, при получении
второго сигнала потоки завершают свою работу.
Второе приложение – консольное приложение Windows (запускается
только при запущенном первом приложении). После нажатия клавиши
посылается сигнал для начала работы потоков в первом приложении. После
следующего нажатия клавиши посылается сигнал на завершение работы потоков
в первом приложении.
Продемонстрировать совместную работу двух приложений.

Алгоритм шагов:

1. Импортировать необходимые заголовочные файлы `Windows.h`, `conio.h`, `iostream` и `locale.h`.
2. Определить функцию `main()`.
3. Установить локаль для поддержки русского языка с помощью `setlocale(LC_ALL, "rus")`.
4. Объявить переменную типа `HANDLE` для хранения дескриптора события `hEvent`.
5. Вызвать функцию `OpenEvent()` для открытия события с именем `"MyEventl"`. Указать флаги доступа `EVENT_ALL_ACCESS` и установить флаг `TRUE` для создания события, если оно не существует.
6. Проверить, успешно ли открыто событие. Если значение `hEvent` равно 0, вывести сообщение об ошибке открытия события в другом приложении, и завершить программу с помощью `_getch()`.
7. Входить в бесконечный цикл `while (true)` для отображения меню.
8. Вывести на экран опции меню: "1 - Запуск потоков" и "2 - Завершение потоков".
9. Очистить буфер ввода с помощью `fflush(stdin)`.
10. Считать выбор пользователя в переменную `sw` с помощью `cin`.
11. Внутри условного оператора `if-else` проверить выбор пользователя:    - Если `sw` равно 1, вывести сообщение "Запускаем..." и вызвать функцию `SetEvent(hEvent)` для установки события.
    - Если `sw` равно 2, вывести сообщение "Завершаем...", вызвать функцию `ResetEvent(hEvent)` для сброса события и завершить программу с помощью `return 0`.    - Если выбрана другая опция, завершить программу с помощью `return 0`.
12. Завершить программу после выхода из цикла.
Таким образом, данный код представляет собой простое меню, позволяющее пользователю запускать и завершать потоки с помощью события.
