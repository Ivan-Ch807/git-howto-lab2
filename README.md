# Git HowTo Lab 2 — TypeScript Utility Library

Лабораторна бібліотека TypeScript-утиліт. Демонструє роботу з `package.json`, розділенням `dependencies`/`devDependencies`, суворою типізацією, валідацією `.env` через `zod`, Git-хуками (`Husky`, `Commitlint`, `ESLint`, `Prettier`) та SemVer.

---

## Швидкий старт

```bash
npm i           # Встановлення залежностей
npm run demo    # Запуск демо
npm run build   # Збірка (CJS, ESM, .d.ts у dist/)

# Перевірки якості
npm run typecheck && npm run lint && npm run format:check
```

---

## Версіонування (SemVer)

- **v0.1.0** — Базові утиліти `add`, `capitalize` (`any`).
- **v0.2.0** — Додано типи `number`, `string`.
- **v0.3.0** — Додано `NumberFormatOptions` та `formatNumber`.
- **v0.4.0** — Додано інтерфейс `User` та `groupBy<T>`.
- **v0.5.0** — Додано клас `Logger` та валідацію `.env` через `zod`.
- **v1.0.0** — Стабілізація API: реекспорти в `index.ts`, заборона `any`, `exports` у `package.json`.
- **v2.0.0** — **Breaking change**: `add` приймає масив `number[]` замість двох аргументів.

---

## Змінні оточення (.env)

Файл `.env` (в `.gitignore`):

```env
APP_PRECISION=3 # 0..10 (за замовчуванням: 2)
LOG_LEVEL=debug # 'silent' | 'info' | 'debug' (за замовчуванням: 'info')
```

---

## Використання

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

## Релізи

[GitHub Releases & Tags](https://github.com/Ivan-Ch807/git-howto-lab2/tags)
