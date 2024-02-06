# Windows 10/11 Optimization
This is a VERY SIMPLE guide suitable for all users with Windows 10/11, version no lower than 20H1.  
This guide utilizes files and methods developed by other users.

## Windows Activation

To activate Windows, follow these steps:

1. Press `WIN + R` and type `CMD`.
2. Depending on your version of Windows, enter the following commands in the console one by one:

   ### For Home:
   ```
   slmgr /ipk TX9XD-98N7V-6WMQ6-BX7FG-H8Q99
   slmgr /skms kms.xspace.in
   slmgr /ato
   ```
   ### For Pro:
   ```
   slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
   slmgr /skms kms.xspace.in   
   slmgr /ato
   ```
     > If activation fails, try replacing the second command with one of the following:
       ```slmgr /skms kms.digiboy.ir```
       ```slmgr /skms zh.us.to```

<hr>

## Getting Started
### Installing Necessary Programs:

1. **Optimization Archive** [Download Archive](https://github.com/uzyanbaev/minimum-latency-windows/files/14055996/optimization.zip)
> If unable to install, here is a second link: [Download Archive](https://drive.google.com/file/d/1IQX7x9KiDELF0Ze8mvYjV2JSp9eUBuro/view?usp=sharing)

2. **DirectX**
[Download DirectX](https://www.microsoft.com/ru-ru/download/details.aspx?id=35)
3. **Microsoft Visual C++ PACK**
[Download Microsoft Visual C++ PACK](https://github.com/abbodi1406/vcredist/releases/tag/v0.77.0)

### Configuring Windows Settings:

1. Open "Start" and enter "Graphics Settings".
2. Enter the section and enable hardware acceleration.

---

## Optimization:
For optimization, use [BoosterX](https://boosterx.org/ru/). The program is intuitive to use.  
With this program, you can easily configure a wide range of system parameters, starting from disabling the high precision event timer to removing unnecessary devices in the device manager. This allows for full system optimization without the need to manually change many settings. Hence, this documentation does not include manual disabling of individual features or services.
### Manual Registry Optimization:
> Since not all settings are available for free in BoosterX, some of them will have to be configured manually.

**Win32Priority**
1. Open the registry by pressing `Win + R` and typing `regedit`.
2. Navigate to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\PriorityControl`.
3. Find the `Win32Priority` parameter and set its value to `2a`.

**NetworkThrottlingIndex**
1. Open the registry by pressing `Win + R` and typing `regedit`.
2. Navigate to `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`.
3. Find the `NetworkThrottlingIndex` parameter and set its value to `a`.

**SystemResponsiveness**
1. Open the registry by pressing `Win + R` and typing `regedit`.
2. Navigate to `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`.
3. Find the `SystemResponsiveness` parameter and set its value to `0`.

---

## Reducing Latency and Eliminating Freezes
> Find the folder `Снижение задержки` in the archive.

**Check Current Latency Values:**
1. Go to the `Снижение задержки` folder.
2. Open the file `dpclat`.
3. Remember the values.
  
**Lowering Latency**
1. Go to the `Снижение задержки` folder.
2. Open the file `68WAntiLagApp`.
3. Click `Enable AntiLag`.
4. Restart the system.
  
**Check Values After**
1. Go to the `Снижение задержки` folder.
2. Open the file `dpclat`.
3. Check that the values have improved.

---

## MSI Mode Tool:
> Find the folder `Msi Mode Tool` in the archive.

1. Open the file `Msi Mode Tool`.
2. Find your graphics card.
3. Check the `MSI` box for your graphics card.
4. Find `USB xHCI Host Controller` (it varies for everyone).
5. Check the `MSI` box for `USB xHCI Host Controller`.

---

## Interrupts:
> Find the folder `Прерывания` in the archive.

**Finding the Best Core for Graphics Card**
1. Open the `Прерывания` folder.
2. Open the file `AutoGpuAffinityRU`.
3. Enter the recommended values.
4. Wait for the test to finish.
5. At the end of the test, the program will find the most suitable core for the graphics card.

**Finding the Host Controller**
> We need to find the host controller to which the mouse is connected.

1. Run `Device Manager`.
2. In the top panel, select `View` and then `Devices by connection`.
3. Find `PCI Express Root Complex`.
4. Expand `PCI Express Root Complex` and find several `PCI Express Root Port`.
5. At one of the `PCI Express Root Port`, we find an `Extended Host Controller` to which our mouse is connected.
6. When we find the host controller to which the mouse is connected, we click on the properties of this host controller.
![image](https://github.com/uzyanbaev/minimum-latency-windows/assets/108973583/300e2342-030b-4322-b67c-9a07cf6e1067)

7. We see `Location` in my case 10, 0, 3.
8. Remember it.

**Setting Core on Host Controller**
1. Open the `Прерывания` folder.
2. Open the file `Interrupt Affinity Policy Tool`.
3. In this program, we need to find the appropriate host controller by Location Info, in my case 10, 0, 3.
![image](https://github.com/uzyanbaev/minimum-latency-windows/assets/108973583/b53bd767-1dea-4294-8915-06f2ce4f59b4)
4. When we find the appropriate host controller, click `Set Mask`.
5. Set any core (`0`, `2`, `4`, `6`, `8`, `10`, etc.) excluding core `0` and the graphics card core.
6. Click OK.
7. Restart the computer.

# End


