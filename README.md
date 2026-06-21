# Navigation 3 — материалы доклада

Материалы внутреннего доклада для мобильных инженеров **Dodo Engineering**.
Тема: Jetpack **Navigation 3** — основы и итеративная миграция с Navigation 2.

> 🌐 **Слайды онлайн:** **https://kartollikaa.github.io/navigation-3-slides/**

Доклад состоит из двух потоков:

1. **Основы Nav3** — модель back stack, сцены, анимации, декораторы.
2. **Миграция Nav2 → Nav3** — итеративный переход «островами», от листьев к корню, без big-bang.

> Целевая версия Navigation 3 — стабильная **1.1.2** (`compileSdk 36`), только Jetpack Compose, ручной DI в стиле Dagger.

---

## Состав репозитория

| Файл / папка | Описание |
| --- | --- |
| `Navigation 3 — доклад (Dodo style).pptx` | Итоговая колода в фирменном стиле Dodo (белый минимализм, индиго `#5B4EE6` + розовый). |
| `Navigation 3 — основы и миграция.pptx` | Ранняя версия колоды. |
| `Navigation 3 — план доклада.md` | План доклада, сверенные факты по API и спикер-заметки (30 слайдов). |
| `references/` | Референсы оформления слайдов (Mobius — Shared Transitions и др.). |
| `nav3-showcase.bundle` | Git-бандл демо-проекта с кодом примеров (см. ниже). |

---

## Демо-проект с кодом

Примеры кода к докладу живут в отдельном репозитории:

**https://github.com/kartollikaa/nav3-showcase**

Это multi-module проект на Compose. Ветки идут по шагам доклада:

- `flow1/01-basics` … `flow1/04-animations` — основы Nav3;
- `flow2/01-nav2-baseline` … `flow2/05-navgraph-plugin` — миграция Nav2 → Nav3.

На каждой ветке есть `BRANCH.md` с пояснениями и спикер-подсказками.

### Восстановление из бандла

Если нужен снимок проекта без доступа к GitHub, разверните локальную копию из `nav3-showcase.bundle`:

```bash
git clone nav3-showcase.bundle nav3-showcase
cd nav3-showcase
git branch -a   # все ветки flow1/* и flow2/*
```

---

> Демо-проект (`nav3-showcase-repo/`) намеренно **не** включён в этот репозиторий — он уже опубликован на GitHub. Здесь хранятся только материалы доклада.
