Экспорт драйверов:
```
# Указываем директорию для бэкапа драйверов
$backupDir = "C:\Backup\Drivers"

# Экспортируем драйверы в указанную директорию
Export-WindowsDriver -Online -Destination $backupDir

Write-Output "Экспорт драйверов завершен..."
```

Установка драйверов:
```
# Указываем директорию с бэкапом драйверов
$backupDir = "C:\Backup\Drivers"

# Получаем список всех драйверов (.inf файлов) в директории
$drivers = Get-ChildItem -Path $backupDir -Filter *.inf -Recurse

# Импортируем каждый драйвер
foreach ($driver in $drivers) {
    pnputil.exe /add-driver $driver.FullName /install
}

Write-Output "Установка драйверов завершена..."
```
