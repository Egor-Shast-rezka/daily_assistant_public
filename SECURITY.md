# Security policy

Daily Assistant stores personal data, so security reports are welcome and
handled with priority.

## Reporting a vulnerability

Please do not open a public issue for a vulnerability. Use
[private vulnerability reporting](https://github.com/Egor-Shast-rezka/daily_assistant/security/advisories/new)
on GitHub instead, and include:

- what is affected: the core, the browser application, the administration
  panel or the home server setup;
- steps to reproduce, with synthetic data only;
- what an attacker gains.

You will receive an answer within seven days. Fixes are released before the
details are published.

## Scope

In scope: the encryption of stored data, login and sessions, the second
factor, key rotation, backups, the certificate authority and the protection
of every web route. The threat model, including what is deliberately not
protected, is described in [docs/THREAT_MODEL.md](docs/THREAT_MODEL.md).

---

# Политика безопасности

Сообщения об уязвимостях отправляйте через
[закрытое сообщение об уязвимости](https://github.com/Egor-Shast-rezka/daily_assistant/security/advisories/new)
на GitHub, а не через открытый issue. Укажите, что затронуто, как
воспроизвести на синтетических данных и что получает атакующий. Ответ - в
течение семи дней, исправление выходит до публикации подробностей.
