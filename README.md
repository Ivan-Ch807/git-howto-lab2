# Git HowTo Lab 2 — TypeScript Utility Library

Лабораторная библиотека TypeScript-утилит. Демонстрирует работу с `package.json`, разделением `dependencies`/`devDependencies`, строгой типизацией, валидацией `.env` через `zod`, Git-хуками (`Husky`, `Commitlint`, `ESLint`, `Prettier`) и SemVer.

---

## Быстрый старт

```bash
npm i           # Установка зависимостей
npm run demo    # Запуск демо
npm run build   # Сборка (CJS, ESM, .d.ts в dist/)

# Проверки качества
npm run typecheck && npm run lint && npm run format:check
```

---

## Версионирование (SemVer)

- **v0.1.0** — Базовые утилиты `add`, `capitalize` (`any`).
- **v0.2.0** — Добавлены типы `number`, `string`.
- **v0.3.0** — Добавлены `NumberFormatOptions` и `formatNumber`.
- **v0.4.0** — Добавлен интерфейс `User` и `groupBy<T>`.
- **v0.5.0** — Добавлен класс `Logger` и валидация `.env` через `zod`.
- **v1.0.0** — Стабилизация API: реэкспорты в `index.ts`, запрет `any`, `exports` в `package.json`.
- **v2.0.0** — **Breaking change**: `add` принимает массив `number[]` вместо двух аргументов.

---

## Переменные окружения (.env)

Файл `.env` (в `.gitignore`):

```env
APP_PRECISION=3 # 0..10 (по умолчанию: 2)
LOG_LEVEL=debug # 'silent' | 'info' | 'debug' (по умолчанию: 'info')
```

---

## Использование

```typescript
import { add, capitalize, formatNumber, groupBy, Logger, type User } from './src/index';

console.log(add([2, 3, 4])); // 9 (v2.0.0)
console.log(capitalize('hello')); // 'Hello'
console.log(formatNumber(123.4567, { precision: 2 })); // '123.46'

const users: User[] = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
];
console.log(groupBy(users, 'name'));

const logger = new Logger('debug');
logger.info('Started');
```

---

## Релизы

[GitHub Releases & Tags](https://github.com/Ivan-Ch807/git-howto-lab2/tags)
