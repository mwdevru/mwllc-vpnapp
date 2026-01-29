# BUILD

Краткие правила сборки и публикации для MW LLC VPN.

## Общие требования
- Windows 10/11 x64
- Flutter SDK (актуальная стабильная версия)
- Git

## Windows (EXE + Installer)
1) Сборка приложения:
```
C:\Users\Mark\Desktop\flutter\bin\flutter build windows
```

2) Сборка установщика Inno Setup:
```
"C:\Program Files (x86)\Inno Setup 6\ISCC.exe" "C:\Users\Mark\Desktop\mwllc-vpn\installer\mwllc_vpn.iss"
```

Результат:
```
C:\Users\Mark\Desktop\mwllc-vpn\installer\build\installer\MWLLC-VPN-Setup.exe
```

## Android (APK)
1) Сборка APK:
```
flutter build apk --release
```

Результат:
```
<project>\build\app\outputs\flutter-apk\app-release.apk
```

## Android (AAB для Google Play)
1) Сборка AAB:
```
flutter build appbundle --release
```

Результат:
```
<project>\build\app\outputs\bundle\release\app-release.aab
```

## macOS
```
flutter build macos --release
```

## iOS
```
flutter build ios --release
```
Дальше архив/подпись через Xcode.

## Linux
```
flutter build linux --release
```

## Версионирование
- Увеличивай версию в `pubspec.yaml`.
- Обновляй `AppVersion` в `installer/mwllc_vpn.iss`.
- Обновляй `kAppVersion` в `lib/main.dart`.

## Авто‑обновление (Windows)
Приложение проверяет GitHub Releases при запуске.
Для корректного обновления:
1) Создай Release с тегом `vX.Y.Z`.
2) Добавь ассет `MWLLC-VPN-Setup.exe`.
3) В тексте релиза добавь строку:
```
SHA256: <hash>
```
