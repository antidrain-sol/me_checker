# ME CHECKER

**ME CHECKER** — это утилита для многопоточной проверки наличия дропов на кошельках. Программа поддерживает различные форматы кошельков и позволяет настраивать параметры многопоточности.

## Основные возможности
- Проверка наличия дропов на кошельках.
- Поддержка нескольких форматов кошельков:
  - `sol` (Solana)
  - `evm` (EVM-совместимые сети)
  - `btc_hex` (Bitcoin в формате hex)
  - `btc_wif` (Bitcoin в формате WIF)
- Настраиваемая многопоточность для повышения производительности.
- Поддержка HTTP(S) Socks(4/5) прокси
---

## Конфигурация

Для работы программы используется конфигурационный файл со следующими параметрами:

### Параметры:
- **`main_solana_wallet`**: Приватный ключ основного кошелька Solana (обязательный параметр).  
  Используется для подписей и взаимодействия с сетью Solana.

- **`max_threads`**: Максимальное количество потоков для выполнения проверок (по умолчанию: `100`).  
  Оптимизируйте значение под возможности вашего оборудования.

### Структура данных:
- **`data/accounts`**: Путь к папке с файлами, содержащими списки кошельков. Файлы должны быть в следующих форматах:
  - `sol.txt` — Solana-кошельки.
  - `evm.txt` — Ethereum/EVM-совместимые кошельки.
  - `btc_hex.txt` — Bitcoin-кошельки в формате hex.
  - `btc_wif.txt` — Bitcoin-кошельки в формате WIF.

---

## Установка и запуск

### Шаг 1: Клонирование репозитория
```bash
git clone <ссылка на репозиторий>
cd me-checker
```

### Шаг 2: Настройка конфигурации
- Отредактируйте файл `data/config.toml` в корневой папке проекта, указав параметры, как показано выше.
- Добавьте файл прокси `data/proxy.txt`. **ОБЯЗАТЕЛЬНО!!!**
### Шаг 3: Запуск программы
```bash
   bun index.ts
```

---

## Пример использования

1. Укажите приватный ключ основного кошелька Solana в конфиге:
   ```ini
   main_solana_wallet = "ВАШ_ПРИВАТНЫЙ_КЛЮЧ"
   max_threads = 50
   ```

2. Добавьте файлы с кошельками в папку `data/accounts`:
   ```plaintext
   data/accounts/sol.txt
   data/accounts/evm.txt
   data/accounts/btc_hex.txt
   data/accounts/btc_wif.txt
   ```
3. Подготовьте среду исполнения программы: https://bun.sh/docs/installation

3. Запустите программу:
   ```bash
   bun index.ts
   ```

---

## Рекомендации по производительности

- Увеличение параметра `max_threads` позволяет ускорить процесс проверки, но может повысить нагрузку на процессор и сеть.