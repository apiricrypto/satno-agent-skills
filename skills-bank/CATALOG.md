# SATNO Skill Bank

بانک Skillهای متن‌باز منتخب برای پروژه‌های SATNO.

## Tier A — اولویت فوری

| Skill | منبع | مجوز | کاربرد در SATNO | اولویت |
|---|---|---|---|---|
| Supabase | supabase/agent-skills → skills/supabase | MIT | دیتابیس، Auth، RLS، Storage و migrationهای CRM | Critical |
| WordPress Router | WordPress/agent-skills → skills/wordpress-router | GPL-2.0-or-later | مسیریابی صحیح وظایف WordPress | High |
| WP Project Triage | WordPress/agent-skills → skills/wp-project-triage | GPL-2.0-or-later | تشخیص نوع پروژه و ابزارهای موجود | High |
| WP Plugin Development | WordPress/agent-skills → skills/wp-plugin-development | GPL-2.0-or-later | توسعه امن Tender Radar | Critical |
| WP REST API | WordPress/agent-skills → skills/wp-rest-api | GPL-2.0-or-later | API و اتصال CRM/WordPress | High |
| WP-CLI & Ops | WordPress/agent-skills → skills/wp-wpcli-and-ops | GPL-2.0-or-later | عملیات، مهاجرت و اتوماسیون WordPress | High |
| WP Performance | WordPress/agent-skills → skills/wp-performance | GPL-2.0-or-later | عیب‌یابی سرعت satnoco.ir | High |
| Playwright CLI | microsoft/playwright → packages/playwright-core/src/tools/skills/playwright-cli | Apache-2.0 | تست رابط و اتوماسیون مرورگر | High |

## Tier B — کاندیدهای ارزشمند بعدی

از WordPress رسمی:
- wp-block-development
- wp-block-themes
- wp-interactivity-api
- wp-abilities-api
- wp-abilities-audit
- wp-abilities-verify
- wp-phpstan
- wp-playground
- wp-env
- wp-plugin-directory-guidelines

## Skillهای اختصاصی SATNO

- satno-crm-developer
- satno-bale-market
- satno-tender-radar
- satno-solar-engineering
- satno-brand
- frontend-design
- webapp-testing
- mcp-builder
- skill-creator-openai
- skill-bank-manager

## سیاست بانک

پیش‌فرض، نگهداری به‌صورت upstream-reference است تا Skillهای رسمی با نسخه‌های جدید قابل sync باشند. Vendoring فقط وقتی انجام می‌شود که استفاده آفلاین یا self-contained لازم باشد و فایل مجوز/اعلان لازم نیز همراهش قرار گیرد.
