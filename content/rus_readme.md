# Оптимизация Windows 10/11
Это ОЧЕНЬ ПРОСТОЕ руководство по оптимизации подходит для всех пользователей с Windows 10/11, версия Windows не ниже 20H1. <br>
В этом руководстве используются файлы и методы, разработанные другими пользователями.

## Активация Windows

Для активации Windows выполните следующие шаги:

1. Нажмите `WIN + R` и введите `CMD`
2. В зависимости от вашей версии Windows, введите поочередно следующие команды в консоль:

   ### Для Home:
   ```
   slmgr /ipk TX9XD-98N7V-6WMQ6-BX7FG-H8Q99
   slmgr /skms kms.xspace.in
   slmgr /ato
   ```
   ### Для Pro:
   ```
   slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
   slmgr /skms kms.xspace.in   
   slmgr /ato
   ```
     > Если активация не удалась, попробуйте заменить вторую команду на одну из следующих:
       ```slmgr /skms kms.digiboy.ir```
       ```slmgr /skms zh.us.to```

<hr>

## Начало
### Установка необходимых программ:

1. **Архив для оптимизации** [Скачать архив](https://github.com/uzyanbaev/minimum-latency-windows/files/14055996/optimization.zip)
> Если не удалось установить, вот вторая ссылка: [Скачать архив](https://drive.google.com/file/d/1IQX7x9KiDELF0Ze8mvYjV2JSp9eUBuro/view?usp=sharing)

2. **DirectX**
[Скачать DirectX](https://www.microsoft.com/ru-ru/download/details.aspx?id=35)
3. **Microsoft Visual C++ PACK**
[Скачать Microsoft Visual C++ PACK](https://github.com/abbodi1406/vcredist/releases/tag/v0.77.0)

### Настройка параметров Windows:

1. Откройте "Пуск" и введите "Настройки графики"
2. Войдите в раздел и включите аппаратное ускорение

<hr>

## Оптимизация:
Для оптимизации используйте [BoosterX](https://boosterx.org/ru/). Программа интуитивно понятна в использовании. <br>
С помощью этой программы можно легко настроить широкий спектр параметров системы, начиная допустим от отключения высокоточного таймера событий и заканчивая удалением ненужных устройств в диспетчере устройств. Это позволяет полностью оптимизировать систему без необходимости вручную изменять множество настроек. Именно поэтому в этой документации нет ручного отключения отдельных функций или служб.
### Ручная оптимизация реестра:
> Поскольку не все параметры доступны бесплатно в BoosterX, некоторые из них придется настроить вручную

**Win32Priority**
  1. Откройте реестр, нажав `Win + R` и введя `regedit`
  2. Перейдите к `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\PriorityControl`
  3. Найдите параметр `Win32Priority` и установите его значение на `2a`

**NetworkThrottlingIndex**
  1. Откройте реестр, нажав `Win + R` и введя `regedit`.
  2. Перейдите к `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`
  3. Найдите параметр `NetworkThrottlingIndex` и установите его значение на `a`
 
**SystemResponsivness**
  1. Откройте реестр, нажав `Win + R` и введя `regedit`.
  2. Перейдите к `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`
  3. Найдите параметр `SystemResponsiveness` и установите его значение на `0`

<hr>

## Снижение задержки и устранение фризов
> Находим в архиве папку `Снижение задержки`

**Проверяем текущие значения задержки:**
  1. Заходим в папку `Снижение задержки`
  2. Открываем файл `dpclat`
  3. Запоминанем
     
**Понижаем задержку**
  1. Заходим в папку `Снижение задержки`
  2. Открываем файл `68WAntiLagApp`
  3. Нажимаем `Enable AntiLag`
  4. Перезапускаем систему
     
**Проверяем значения после**
  1. Заходим в папку `Снижение задержки`
  2. Открываем файл `dpclat`
  3. Проверяем, что значения стали лучше

<hr>

## MSI Mode Tool:
> Находим в архиве папку `Msi Mode Tool`

1. Открываем файл `Msi Mode Tool`
2. Находим видеокарту
3. Ставим галочку `MSI` на видеокарту
4. Находим `USB xHCI Host Controller` (примерно так, у всех по разному)
5. Ставим галочку `MSI` на `USB xHCI Host Controller`

<hr>

## Прерывания:
> Находим в архиве папку `Прерывания`

**Находим лучшее ядро для видеокарты**
1. Открываем папку `Прерывания`
2. Открываем файл `AutoGpuAffinityRU`
3. Вводим рекомендуемые значения
4. Ожидаем окончания теста
5. По окончании теста программа найдет наиболее подходящее ядро для видеокарты

**Находим хост-контроллер**
> Мы должны найти хост-контроллер, к которому подключена мышь

1. Запускаем `Диспетчер устройств`
2. В верхней панели выбираем `Вид` и ставим `Устройства по подключению`
3. Находим `PCI Express Root Complex`
4. Раскрываем `PCI Express Root Complex` и находим несколько `Порт PCI Express Root`
5. У какого-то `Порт PCI Express Root` мы находим `Расширяемый хост-контроллер` к которому подключена наша мышь
6. Когда найдем хост-контроллер, к которому подключена мышь, нажимаем на свойства этого хост-контроллера
![image](https://github.com/uzyanbaev/minimum-latency-windows/assets/108973583/300e2342-030b-4322-b67c-9a07cf6e1067)

7. Видим `Размещение` в моем случае 10, 0, 3
8. Запоминаем

**Ставим ядро на хост-контроллер**
1. Открываем папку `Прерывания`
2. Открываем файл `Interrupt Affinity Policy Tool`
3. В этой программе мы должны найти подходящий хост-контроллер по Location Info, в моем случае 10, 0, 3
![image](https://github.com/uzyanbaev/minimum-latency-windows/assets/108973583/b53bd767-1dea-4294-8915-06f2ce4f59b4)
4. Когда найдем подходящий хост-контроллер, нажимаем `Set Mask`
5. Ставим любое ядро `0`, `2`, `4`, `6`, `8`, `10` и т.д.) исключая ядро `0` и ядро видеокарты
6. Нажимаем OK
7. Перезагружаем компьютер

# Конец
