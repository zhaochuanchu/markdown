* 通用设备系列是特殊系列。 它并非任意操作系统的直接基础构件。 相反， **通用设备系列中的 API 集由子设备系列继承** 。 因此，通用设备系列 API 保证能存在于每个操作系统中和每台设备上
* 将dll导入工程必须放到Assets\Plugins(\WSA)路径下。Unity会自动识别。如果放到其它文件夹，Unity会将其视为普通dll，报错（.net4.x版本的dll，必须为.net3.5或以下版本)
* 关于Unity发布UWP的问题，一定要多读读Unity的官方文档，很多问题确实百度不出来的。