# telegram-bot-open-ai

Простой Telegram-бот на **aiogram 3** с интеграцией **OpenAI API** — отвечает на сообщения пользователя через модель OpenAI по команде.

## Возможности

- `/start` — приветственное сообщение.
- `/chat <текст>` — отправляет текст пользователя в OpenAI и возвращает сгенерированный ответ в чат.
- Пара дополнительных demo-команд с фиксированными текстовыми ответами (легко редактируются под свои нужды).

## Стек

- Python 3
- [aiogram 3](https://docs.aiogram.dev/) — асинхронный Telegram Bot API
- [openai](https://pypi.org/project/openai/) — обращение к API OpenAI

## Установка

```bash
git clone https://github.com/xishe/telegram-bot-open-ai.git
cd telegram-bot-open-ai
pip install aiogram openai
```

## Настройка

В `main.py` нужно указать два ключа:

```python
openai.api_key = "open-ai-api-key"  # API-ключ OpenAI
...
bot = Bot("API - KEY")  # токен Telegram-бота
```

- Токен Telegram-бота получается у [@BotFather](REDACTED_CONTACT).
- API-ключ OpenAI — в [личном кабинете OpenAI](https://platform.openai.com/api-keys).

Для продакшена ключи лучше вынести в переменные окружения / `.env`-файл, а не хранить в коде.

## Запуск

```bash
python main.py
```

Бот запускается в режиме long polling.

## Структура проекта

```
telegram-bot-open-ai/
├── main.py       # логика бота: команды, интеграция с OpenAI
└── README.md
```

## Важное примечание

Бот использует устаревший эндпоинт `openai.Completion.create` с моделью `text-davinci-003` (legacy Completions API). Этот эндпоинт и модель уже выведены OpenAI из эксплуатации — для работы бота команду `/chat` нужно переписать под актуальный **Chat Completions API** (`openai.ChatCompletion.create` / `client.chat.completions.create` в новых версиях SDK) и современную модель (например, `gpt-4o-mini` или другую доступную на момент использования).

## Автор

by x1she
