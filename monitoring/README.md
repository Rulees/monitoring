# Описание

Данный репозиторий используется для управления мониторингом всех проектов.



# С чего начать?

* **[ (docs/QUICKSTART.md)](docs/QUICKSTART.md)** — Читайте это, если хотите прямо сейчас добавить мониторинг для своего проекта. 

* **[(docs/ARCHITECTURE.md)](docs/ARCHITECTURE.md)** — Читайте это, если хотите глубоко понять, как устроена инфраструктура.



# Быстрый обзор


  ```plaintext
  │
  ├──🔧 playbook.yml
  │
  │ === ИНФРАСТРУКТУРНЫЙ УРОВЕНЬ ===
  ├──📁 10-exporters                                   -- Источники (Где рождаются данные: blackbox, domains)
  ├──📁 20-collectors                                  -- Транспорт (Кто собирает и несет в базу: vmagent, promtail)
  ├──📁 30-databases                                   -- Хранилища (Где данные лежат: prometheus, loki)
  ├──📁 40-frontend                                    -- Визуализация (Настройки UI: grafana, plugins)
  │
  │ === БИЗНЕС-УРОВЕНЬ ===
  ├──🌍 global                                         -- Глобальные правила для всех проектов
  │   ├──📁 alerts
  │   │   └──📄 infra.alerts.yml
  │   ├──📁 dashboards
  │   │   ├──📄 cpu_mem_disk.json
  │   │   └──📄 ssl_domain_expires.json
  │   └──📁 metadata
  │       ├──📄 deploy_tags.rules.yml
  │       └──📄 vars_canary_and_stable.json
  │
  ├──📖 docs
  │   └──📦 _examples-templates                        -- СПРАВОЧНИК ЭТАЛОНОВ (Только для чтения и копирования)
  │       ├──📁 nginx
  │       │   ├──📄 alerts.yml                         
  │       │   ├──📄 dashboard.json                     
  │       │   └──📄 rules.yml                          
  │       └──📁 telegrambot
  │           ├──📄 alerts.yml                         
  │           ├──📄 dashboard.json                     
  │           └──📄 rules.yml                          
  └──📁 projects                                           -- PRODUCTION ПРОЕКТЫ (Изолированные рабочие среды)
      ├──📁 asepta
      │   └──📁 nginx
      │       ├──📄 alerts.yml
      │       ├──📄 dashboard.json
      │       └──📄 rules.yml
      ├──📁 bion
      ├──📁 cki
      ├──📁 cmb
      ├──📁 corsar
      ├──📁 mapei
      └──📁 seamless
