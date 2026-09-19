# Amadeus — быстрый доступ

Окно с кнопками: нажали на кнопку — открылся сайт или программа.

## Запуск

Откройте `dist\Amadeus.exe`.

Из исходников (нужен Python 3.10+):

```bash
pip install -r requirements.txt
python main.py
```

## Управление

| Клавиша | Что делает |
|---|---|
| Tab / Shift+Tab | следующая / предыдущая вкладка |
| ← → ↑ ↓ | выбрать кнопку (выбранная обведена белой рамкой) |
| Enter или пробел | открыть выбранное |
| Мышь | тоже работает |

## Как добавить кнопку

1. Откройте `config.py` и добавьте строку в список `SERVICES`.

   Сайт:
   ```python
   {"name": "📺 YouTube", "url": "https://www.youtube.com", "color": "#CC2222", "category": "Social"},
   ```
   Программа (путь к `.exe` или ярлыку `.lnk`):
   ```python
   {"name": "📨 Telegram", "path": r"C:\путь\Telegram.lnk", "color": "#229ED9", "category": "Apps"},
   ```
   `category` — вкладка: `AI`, `Email`, `Social`, `Games` или `Apps`.

2. Закройте Amadeus и пересоберите его (один раз перед этим: `pip install pyinstaller`):
   ```bash
   python -m PyInstaller --noconfirm --clean --onefile --windowed --icon=icon.ico --add-data "icon.ico;." --name Amadeus main.py
   ```
   Новый exe появится в папке `dist`.

## Если что-то не так

- **«Отказано в доступе» при сборке** — Amadeus ещё открыт, закройте его.
- **Кнопка программы выдаёт ошибку** — на этом компьютере программа лежит по другому пути, исправьте `path`.
- **Лишний пробел после эмодзи в названии кнопки** — выберите другой эмодзи (без невидимого символа, например 📺 вместо ▶️).
