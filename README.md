# Sega Genesis P2P

Мультиплеерный эмулятор Sega Mega Drive / Genesis в браузере. Полностью статичный сайт —
связь между монитором (ПК) и геймпадами (телефоны) идёт напрямую через WebRTC
с помощью [Trystero](https://github.com/dmotz/trystero) (стратегия torrent).

- `index.html` — выбор роли: создать комнату (монитор) или войти по коду (геймпад)
- `monitor.html?room=КОД` — эмулятор (EmulatorJS, ядро segaMD), QR-код для геймпадов,
  статус Gamepad 1/2, автозагрузка ROM с emu-land (через CORS-прокси) или ручной выбор файла
- `gamepad.html?room=КОД` — виртуальный геймпад с редактируемой раскладкой

Первый подключившийся геймпад становится Player 1 (порт 0), второй — Player 2 (порт 1).

## Деплой на GitHub Pages

```powershell
cd C:\Users\Neo\CascadeProjects\sega-genesis-p2p
git init
git add .
git commit -m "Sega Genesis P2P"
git branch -M main
git remote add origin https://github.com/<ВАШ_ЛОГИН>/sega-genesis-p2p.git
git push -u origin main
```

Затем в репозитории: **Settings → Pages → Source: Deploy from a branch → Branch: main / (root) → Save**.

Через пару минут сайт будет доступен по адресу
`https://<ВАШ_ЛОГИН>.github.io/sega-genesis-p2p/`.

HTTPS (который даёт GitHub Pages) обязателен — WebRTC и ES-модули работают только по
защищённому соединению.

## Локальная проверка

```powershell
cd C:\Users\Neo\CascadeProjects\sega-genesis-p2p
python -m http.server 8080
```

Открыть `http://localhost:8080/` — но полноценный P2P между разными устройствами
требует HTTPS-деплой.
