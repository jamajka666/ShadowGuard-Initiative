# ShadowGuard Working Library

Working odpovídá na otázku: **Jak to děláme teď?**

Tyto manuskripty se smí často měnit. Jsou praktické, technické a časově vázané.

## Katalog (aktuální + plánovaný)

| ID | Název | Účel | Stav |
|----|--------|------|------|
| SGW-001 | Sprint 0 | Příprava prostředí, checklisty spuštění | plán |
| [SGW-002](SGW-002-Roadmap.md) | Roadmap | Fáze, tempo, milníky | **živý** |
| SGW-003 | Architecture Truth | Shadvert vs. referenční engine, data flow | plán |
| SGW-004 | Prompt Library | Prompty, JSON schémata, testovací sady | plán |
| [SGW-005](SGW-005-Security-Audit.md) | Security Audit | Nálezy a nápravy Shadvert | **živý** |
| [SGW-006](SGW-006-Definition-of-Done.md) | Definition of Done | Quality bar, P-štítky, Beta Rule | **živý** |
| [SGW-007](SGW-007-Feature-Trust-Gate.md) | Feature Trust Gate | Checklist důvěry před merge funkce | **živý** |

## Oddělení od Foundation

| Foundation | Working |
|------------|---------|
| Proč | Jak |
| Stabilní | Proměnlivé |
| Hodnoty a závazky | Sprinty a technika |
| Revize vzácné | Aktualizace běžné |

## Aktuální fokus — Trust Sprint (od 2026-08-06)

1. ~~Foundation jádro + Trust Principles + Design~~ — v gitu.  
2. **Delta security** → [SGW-005](SGW-005-Security-Audit.md).  
3. **Stabilita + Trust Engine MVP** (hybrid, golden, cache).  
4. **Jednoduchý režim** jen flag/closed (D-019, D-021).  
5. **Closed beta** táta + 5–10 + feedback (8 otázek).  
6. Gate: [SGW-007](SGW-007-Feature-Trust-Gate.md) · DoD: [SGW-006](SGW-006-Definition-of-Done.md).

Způsob práce: [SGF-002 Way](../Foundation/CZ/SGF-002-ShadowGuard-Way.md) · [SGF-009 Decision Protocol](../Foundation/CZ/SGF-009-Decision-Protocol.md)  
Roadmap: [SGW-002](SGW-002-Roadmap.md)  
**Release Founding Edition: ještě ne** (D-013).