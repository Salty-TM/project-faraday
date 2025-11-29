# ⚡ Project Faraday

> **"Fyziku nelze obejít. Stejně tak nelze obejít právo na soukromí."**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)]()
[![Privacy](https://img.shields.io/badge/privacy-extreme-red)]()

**Project Faraday** je open-source iniciativa vyvíjející decentralizovanou komunikační platformu odolnou vůči hromadnému sledování a legislativě typu "Chat Control" (Client-Side Scanning).

Naším cílem není vytvořit "další chatovací aplikaci", ale poskytnout **Faradayovu klec pro vaše data** – prostor, kam nedosáhnou algoritmy korporací ani vládní slídění.

---

## 🏗️ Architektura: The Cage & The Mesh

Projekt se skládá ze dvou hlavních částí:

1.  **The Cage (Server):** Self-hosted server, který si uživatel provozuje doma (Raspberry Pi, VPS). Je navržen jako "Zero-Knowledge" – server vidí pouze šifrovaný šum, nemá přístup k klíčům a neuchovává logy.
2.  **Faraday (Klient):** Webová (Vue.js) a mobilní aplikace, která zajišťuje **End-to-End šifrování (E2EE)** přímo na zařízení.

```mermaid
graph TD
    A[Alice (Faraday Klient)] -->|1. E2EE Šifrování| B(The Cage - Server Alice)
    B -->|2. Přenos přes Federaci| C(The Cage - Server Bob)
    C -->|3. Push/Doručení| D[Bob (Faraday Klient)]
    D -->|4. Dešifrování| D
    
    subgraph Klíčové Zabezpečení
        K[Privátní Klíče]
    end
    
    K -- Držené výhradně klienty --> A
    K -- Držené výhradně klienty --> D
    
    style B fill:#f2f2f2, stroke:#7C3AED, stroke-width:2px, color:#333;
    style C fill:#f2f2f2, stroke:#0D9488, stroke-width:2px, color:#333;