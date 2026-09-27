# UE-BlueprintAnalyzer

<p align="center">
  <strong>Blueprint analysis and diagnostics for Unreal Engine</strong>
</p>

<p align="center">
  <a href="#lang-en">
    <img src="https://img.shields.io/badge/🇬🇧%20English-ffffff?style=for-the-badge&labelColor=2f2f2f&color=555555" alt="English">
  </a>
  <a href="#lang-ru">
    <img src="https://img.shields.io/badge/🇷🇺%20Русский-ffffff?style=for-the-badge&labelColor=2f2f2f&color=555555" alt="Русский">
  </a>
  <a href="#lang-cz">
    <img src="https://img.shields.io/badge/🇨🇿%20Čeština-ffffff?style=for-the-badge&labelColor=2f2f2f&color=555555" alt="Čeština">
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Unreal%20Engine-5.x-313131?style=flat-square&logo=unrealengine&logoColor=white" alt="Unreal Engine">
  <img src="https://img.shields.io/badge/C%2B%2B-20-00599C?style=flat-square&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/Status-In%20Development-F39C12?style=flat-square" alt="Status">
  <img src="https://img.shields.io/github/license/just1nslyyy/UE-BlueprintAnalyzer?style=flat-square" alt="License">
</p>

---

<a name="lang-en"></a>

# 🇬🇧 English

## UE-BlueprintAnalyzer

**UE-BlueprintAnalyzer** is an Unreal Engine Editor plugin for analyzing Blueprint graphs, dependencies, complexity, and potential structural issues.

The project treats Blueprint logic as a graph of nodes and connections, providing developers with structured information about how their Blueprint systems are built.

The goal is simple:

> **Make Blueprint systems easier to understand, inspect, and maintain.**

## Features

- Blueprint graph analysis
- Node and pin inspection
- Execution flow analysis
- Graph complexity metrics
- Cyclomatic complexity analysis
- Blueprint dependency analysis
- Variable usage analysis
- Structural diagnostics
- Detection of potentially unreachable nodes
- Detection of excessively large graphs
- Detection of deeply nested execution paths
- Native Unreal Editor interface

## Example

```text
Blueprint: BP_Player

Function: ProcessInteraction

Nodes: 48
Edges: 57
Branches: 10

Cyclomatic Complexity: 11

Issues:
  BP001  Large graph
  BP003  Deep branch nesting
  BP007  High cyclomatic complexity
```

## Architecture

```text
                    Blueprint
                        │
                        ▼
                 ┌─────────────┐
                 │ Graph Walker │
                 └─────────────┘
                        │
                        ▼
                 ┌─────────────┐
                 │   Analyzer  │
                 └─────────────┘
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
          Metrics   Diagnostics  Dependencies
             │          │          │
             └──────────┼──────────┘
                        ▼
                Analysis Results
                        │
                        ▼
                    Editor UI
```

The analysis layer is designed to remain independent from the presentation layer, allowing analysis results to be reused by other tools and future integrations.

## Technology

- C++
- Unreal Engine 5
- Unreal Editor APIs
- Blueprint Graph APIs
- Asset Registry
- Slate

## Complexity Analysis

One of the core metrics is **cyclomatic complexity**.

For a graph:

```text
M = number of edges
N = number of nodes
P = number of connected components
```

The complexity can be represented as:

```text
M - N + 2P
```

Example:

```text
Function: ProcessInteraction

Nodes:                  48
Edges:                   57
Branches:                10
Cyclomatic Complexity:   11
```

## Dependency Analysis

The analyzer can represent relationships between Blueprints and referenced assets.

Example:

```text
BP_Player
├── BP_Inventory
│   ├── BP_Item
│   └── BP_Weapon
│
├── BP_Interaction
│   └── BP_Door
│
└── BP_SaveSystem
```

## Design Principles

### Read-only by default

The analyzer inspects project content without unexpectedly modifying user assets.

### Separation of concerns

Graph traversal, analysis rules, result generation, and UI are separate parts of the system.

### Extensibility

New diagnostic rules should be possible without rewriting the analysis core.

### Information over judgement

The tool provides measurable data and diagnostics rather than enforcing a single "correct" Blueprint style.

## Project Status

🚧 **In Development**

UE-BlueprintAnalyzer is being developed as an independent Unreal Engine tooling project focused on editor integration, graph analysis, and clean C++ architecture.

## License

This project is licensed under the **MIT License**.

See [`LICENSE`](LICENSE).

## Disclaimer

UE-BlueprintAnalyzer is an independent community project.

**Unreal Engine** is a trademark of Epic Games, Inc.  
This project is not affiliated with or endorsed by Epic Games.

---

<p align="center">
  <a href="#lang-en">
    <img src="https://img.shields.io/badge/🇬🇧-English-2f2f2f?style=for-the-badge" alt="English">
  </a>
  <a href="#lang-ru">
    <img src="https://img.shields.io/badge/🇷🇺-Русский-2f2f2f?style=for-the-badge" alt="Русский">
  </a>
  <a href="#lang-cz">
    <img src="https://img.shields.io/badge/🇨🇿-Čeština-2f2f2f?style=for-the-badge" alt="Čeština">
  </a>
</p>

---

<a name="lang-ru"></a>

# 🇷🇺 Русский

## UE-BlueprintAnalyzer

**UE-BlueprintAnalyzer** — это плагин для Unreal Engine Editor для анализа Blueprint-графов, зависимостей, сложности и потенциально проблемных структур.

Проект рассматривает Blueprint-логику как граф узлов и связей и предоставляет разработчику структурированную информацию о том, как построена его система.

Цель проекта:

> **Сделать Blueprint-системы проще для понимания, анализа и поддержки.**

## Возможности

- Анализ Blueprint-графов
- Анализ нод и пинов
- Анализ execution flow
- Метрики сложности графа
- Анализ цикломатической сложности
- Анализ зависимостей Blueprint
- Анализ использования переменных
- Структурная диагностика
- Поиск потенциально недостижимых нод
- Поиск слишком больших графов
- Поиск глубоко вложенных execution paths
- Нативный интерфейс внутри Unreal Editor

## Пример

```text
Blueprint: BP_Player

Function: ProcessInteraction

Nodes: 48
Edges: 57
Branches: 10

Cyclomatic Complexity: 11

Issues:
  BP001  Large graph
  BP003  Deep branch nesting
  BP007  High cyclomatic complexity
```

## Архитектура

```text
                    Blueprint
                        │
                        ▼
                 ┌─────────────┐
                 │ Graph Walker │
                 └─────────────┘
                        │
                        ▼
                 ┌─────────────┐
                 │   Analyzer  │
                 └─────────────┘
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
          Metrics   Diagnostics  Dependencies
             │          │          │
             └──────────┼──────────┘
                        ▼
                Analysis Results
                        │
                        ▼
                    Editor UI
```

Слой анализа отделён от слоя отображения, поэтому результаты анализа можно будет использовать в других инструментах и интеграциях.

## Технологии

- C++
- Unreal Engine 5
- Unreal Editor APIs
- Blueprint Graph APIs
- Asset Registry
- Slate

## Анализ сложности

Одной из основных метрик является **цикломатическая сложность**.

Для графа:

```text
M = количество рёбер
N = количество узлов
P = количество связанных компонентов
```

Формула:

```text
M - N + 2P
```

Пример:

```text
Function: ProcessInteraction

Nodes:                  48
Edges:                   57
Branches:                10
Cyclomatic Complexity:   11
```

## Анализ зависимостей

Анализатор может отображать отношения между Blueprint и используемыми ассетами.

Пример:

```text
BP_Player
├── BP_Inventory
│   ├── BP_Item
│   └── BP_Weapon
│
├── BP_Interaction
│   └── BP_Door
│
└── BP_SaveSystem
```

## Принципы

### Read-only по умолчанию

Анализатор исследует содержимое проекта без неожиданных изменений пользовательских ассетов.

### Разделение ответственности

Обход графа, правила анализа, формирование результатов и UI являются отдельными частями системы.

### Расширяемость

Добавление новых диагностических правил не должно требовать переписывания ядра анализатора.

### Информация вместо субъективной оценки

Инструмент предоставляет измеряемые данные и диагностику, а не навязывает один "правильный" стиль Blueprint.

## Статус проекта

🚧 **В разработке**

UE-BlueprintAnalyzer создаётся как независимый инструмент для Unreal Engine с акцентом на интеграцию в редактор, анализ графов и чистую C++-архитектуру.

## Лицензия

Проект распространяется под **MIT License**.

Подробнее: [`LICENSE`](LICENSE).

## Дисклеймер

UE-BlueprintAnalyzer — независимый community-проект.

**Unreal Engine** является товарным знаком Epic Games, Inc.  
Проект не связан с Epic Games и не является официальным инструментом Epic Games.

---

<p align="center">
  <a href="#lang-en">
    <img src="https://img.shields.io/badge/🇬🇧-English-2f2f2f?style=for-the-badge" alt="English">
  </a>
  <a href="#lang-ru">
    <img src="https://img.shields.io/badge/🇷🇺-Русский-2f2f2f?style=for-the-badge" alt="Русский">
  </a>
  <a href="#lang-cz">
    <img src="https://img.shields.io/badge/🇨🇿-Čeština-2f2f2f?style=for-the-badge" alt="Čeština">
  </a>
</p>

---

<a name="lang-cz"></a>

# 🇨🇿 Čeština

## UE-BlueprintAnalyzer

**UE-BlueprintAnalyzer** je plugin pro Unreal Engine Editor určený k analýze Blueprint grafů, závislostí, složitosti a potenciálně problematických struktur.

Projekt pracuje s Blueprint logikou jako s grafem uzlů a propojení a poskytuje vývojářům strukturované informace o tom, jak je jejich systém vytvořen.

Cíl projektu:

> **Usnadnit porozumění, kontrolu a údržbu Blueprint systémů.**

## Funkce

- Analýza Blueprint grafů
- Analýza uzlů a pinů
- Analýza execution flow
- Metriky složitosti grafu
- Analýza cyklomatické složitosti
- Analýza závislostí Blueprintů
- Analýza použití proměnných
- Strukturální diagnostika
- Detekce potenciálně nedosažitelných uzlů
- Detekce příliš velkých grafů
- Detekce hluboce zanořených execution paths
- Nativní rozhraní v Unreal Editoru

## Příklad

```text
Blueprint: BP_Player

Function: ProcessInteraction

Nodes: 48
Edges: 57
Branches: 10

Cyclomatic Complexity: 11

Issues:
  BP001  Large graph
  BP003  Deep branch nesting
  BP007  High cyclomatic complexity
```

## Architektura

```text
                    Blueprint
                        │
                        ▼
                 ┌─────────────┐
                 │ Graph Walker │
                 └─────────────┘
                        │
                        ▼
                 ┌─────────────┐
                 │   Analyzer  │
                 └─────────────┘
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
          Metrics   Diagnostics  Dependencies
             │          │          │
             └──────────┼──────────┘
                        ▼
                Analysis Results
                        │
                        ▼
                    Editor UI
```

Analytická vrstva je oddělena od prezentační vrstvy, takže výsledky analýzy lze později použít i v dalších nástrojích a integracích.

## Technologie

- C++
- Unreal Engine 5
- Unreal Editor APIs
- Blueprint Graph APIs
- Asset Registry
- Slate

## Analýza složitosti

Jednou z hlavních metrik je **cyklomatická složitost**.

Pro graf:

```text
M = počet hran
N = počet uzlů
P = počet propojených komponent
```

Vzorec:

```text
M - N + 2P
```

Příklad:

```text
Function: ProcessInteraction

Nodes:                  48
Edges:                   57
Branches:                10
Cyclomatic Complexity:   11
```

## Analýza závislostí

Analyzátor může zobrazovat vztahy mezi Blueprinty a použitými assety.

Příklad:

```text
BP_Player
├── BP_Inventory
│   ├── BP_Item
│   └── BP_Weapon
│
├── BP_Interaction
│   └── BP_Door
│
└── BP_SaveSystem
```

## Principy

### Ve výchozím stavu pouze pro čtení

Analyzátor prohlíží obsah projektu bez neočekávaných změn uživatelských assetů.

### Oddělení odpovědností

Procházení grafu, analytická pravidla, tvorba výsledků a UI jsou oddělené části systému.

### Rozšiřitelnost

Nová diagnostická pravidla by měla být přidávána bez přepisování jádra analyzátoru.

### Informace místo subjektivního hodnocení

Nástroj poskytuje měřitelná data a diagnostiku místo vynucování jediného "správného" stylu Blueprintů.

## Stav projektu

🚧 **Ve vývoji**

UE-BlueprintAnalyzer vzniká jako nezávislý nástroj pro Unreal Engine se zaměřením na integraci do editoru, analýzu grafů a čistou C++ architekturu.

## Licence

Projekt je distribuován pod **MIT License**.

Podrobnosti: [`LICENSE`](LICENSE).

## Disclaimer

UE-BlueprintAnalyzer je nezávislý community projekt.

**Unreal Engine** je ochranná známka společnosti Epic Games, Inc.  
Projekt není spojen se společností Epic Games ani není oficiálním nástrojem společnosti Epic Games.

---

<p align="center">
  <a href="#lang-en">
    <img src="https://img.shields.io/badge/🇬🇧-English-2f2f2f?style=for-the-badge" alt="English">
  </a>
  <a href="#lang-ru">
    <img src="https://img.shields.io/badge/🇷🇺-Русский-2f2f2f?style=for-the-badge" alt="Русский">
  </a>
  <a href="#lang-cz">
    <img src="https://img.shields.io/badge/🇨🇿-Čeština-2f2f2f?style=for-the-badge" alt="Čeština">
  </a>
</p>
