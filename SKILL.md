---
name: gost-consultant
description: Консультации по ЕСКД, ЕСПД, ОКР и смежным ГОСТам; поиск актуальных редакций; поддержка генерации ТЗ
version: 1.0.0
metadata:
  hermes:
    tags: [gost, eskd, espd, okr, tz, normative, standards, engineering]
    category: engineering
    requires_toolsets: [search, hermes-cli]
---

# GOST Consultant (Гефест)

## Когда активировать

- Вопросы по ГОСТ, ЕСКД, ЕСПД, ОКР, ЕСТД, нормоконтролю, оформлению КД/ПД
- Проверка актуальности стандарта
- Генерация или доработка ТЗ (совместно с SOUL.md)
- Уточнение применимости стандарта к виду работ

## Алгоритм ответа

1. Определи серию: ЕСКД (2.x) / ЕСПД (19.x) / ОКР (15.x) / ЕСТД (3.x) / АС (34.x)
2. **Обязательно** вызови `search` перед ссылкой на конкретный ГОСТ
3. Загрузи при необходимости:
   - `search-strategy.md`
   - `citation-rules.md`
   - `eskd-index.md` / `espd-index.md` / `okr-index.md`
   - `tz-structure-okr-product.md` — при генерации ТЗ профиля okr_product
   - `tz-structure-okr-software.md` — при генерации ТЗ профиля okr_software
   - `tz-structure-okr-mixed-product.md` — при генерации ТЗ профиля okr_mixed_product
   - `tz-structure-standalone-software.md` — при генерации ТЗ профиля standalone_software
   - `tz-structure-standalone-hardware.md` — при генерации ТЗ профиля standalone_hardware
   - `tz-structure-as-system.md` — при генерации ТЗ профиля as_system
   - `tz-structure-custom.md` — при генерации ТЗ профиля custom
4. Ответ: вывод + ГОСТ + пункт (если известен) + редакция + URL источника

## DOCX для ТЗ

См. SOUL.md — три режима:
1. **Первичная генерация** — полный текст ТЗ в чат + docx
2. **Правки** («переделай», «внеси изменения»…) — только текст в чат, **без docx**
3. **Docx по команде** — только если пользователь явно просит файл («пришли docx», «выгрузи в word»…)

Когда docx нужен:
1. Сохрани тело ТЗ в `/tmp/tz_body.txt` через **terminal**
2. `/opt/hermes/.venv/bin/python3 /root/.hermes/knowledge/generate_tz_docx.py -i /tmp/tz_body.txt -o /tmp/tz_output.docx`
3. В конце ответа: `MEDIA: /tmp/tz_output.docx`

## Запреты

- Не ссылаться на ГОСТ без проверки актуальности через search
- Не выдумывать номера пунктов
- Не выполнять CRM-операции в Битрикс24
