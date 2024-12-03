---
tags:
  - pipeline
  - ci
  - dev-ветка
  - деплой_приложения
---

---
#dev-ветка #develop
# dev-ветка

Ветка `develop` — это одна из основных веток в популярных моделях ветвления, таких как **Git Flow**, и она служит для интеграции новых функций, улучшений и исправлений перед выпуском релиза. Ветка `develop` обычно используется как рабочая ветка, куда разработчики регулярно объединяют свои изменения, и её ключевые особенности и предназначение следующие:

1. **Интеграционная ветка**:
    - Ветка `develop` используется для объединения и тестирования всех новых изменений, прежде чем они попадут в основную стабильную ветку (`main` или `master`)
    - Когда разработчик завершает работу над новой функцией или исправлением, он делает pull request и объединяет изменения из своей _feature-ветки_ в `develop`
    
2. **Постоянное обновление и тестирование**:
    - На основе `develop` обычно строится CI (непрерывная интеграция), где каждый новый коммит автоматически запускает тесты и сборку. Это помогает убедиться, что код в `develop` всегда находится в рабочем состоянии
    - Периодически проект может деплоиться в тестовую или стейджинг-среду, чтобы протестировать изменения в условиях, близких к продакшену
    
3. **Подготовка к релизу**:
    - Когда команда готова к выпуску новой версии, от `develop` обычно создаётся ветка релиза (например, `release/1.0`)
    - Ветку релиза используют для окончательных тестов и внесения критических исправлений или доработок
    - `release` - стабильная версия кода приложения, которая разворачивается на проде
    - После завершения подготовки к выпуску ветка релиза объединяется как в `main` (или `master`), так и обратно в `develop`, чтобы синхронизировать код
    
4. **Защита от конфликтов с продакшеном**:
    - В отличие от `main`, `develop` может содержать нестабильный код или код с новыми функциями, которые ещё не готовы для продакшена. Это позволяет разработчикам активно работать над новым функционалом, не влияя на стабильность продакшена

**Основной принцип**: `develop` — это основная ветка для разработки и тестирования до выпуска в продакшен, а `main` предназначена для стабильных релизов.


---
#деплой_приложения #deploy
# Деплой веб-приложения (в разработке)

https://youtu.be/uLp-zgset00

---