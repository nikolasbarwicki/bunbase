Use Bun as the runtime, package manager, test runner, and bundler.

Bun automatically loads .env — don't use dotenv.

## Preferred APIs

- `Bun.serve()` over express
- `bun:sqlite` over better-sqlite3
- `Bun.redis` over ioredis
- `Bun.sql` over pg/postgres.js
- `Bun.file` over node:fs readFile/writeFile
- `Bun.$` over execa
- Built-in `WebSocket` over ws
