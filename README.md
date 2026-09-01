<h1 align="center">Enzo LANDRECY</h1>

<p align="center">
  <b>Développeur backend · Étudiant en Master MIAGE — UT1 Capitole, Toulouse</b>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/enzo-landrecy"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="mailto:enzo.landrecy@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
  <img src="https://img.shields.io/badge/Toulouse-%F0%9F%87%AB%F0%9F%87%B7-1F6FEB?style=for-the-badge" alt="Toulouse">
  <img src="https://img.shields.io/badge/Gen%C3%A8ve%20%E2%80%93%20Lausanne-%F0%9F%87%A8%F0%9F%87%AD-D52B1E?style=for-the-badge" alt="Genève – Lausanne">
</p>

---

## 🧑‍💻 À propos

Étudiant en **Master 1 MIAGE à UT1 Capitole**, orienté **backend et architecture logicielle**. Je travaille surtout sur des APIs, des bases de données et l'industrialisation qui va avec : tests, CI, qualité de code.

En ce moment, je construis **[Lodestone](#-lodestone--assistant-de-connaissances-souverain-pour-entreprises)**, un assistant de connaissances RAG auto-hébergeable écrit en **Rust**. C'est mon projet de fond : conception produit, architecture backend, et une exigence forte sur la qualité (clippy zéro warning, tests d'intégration sur base éphémère).

À côté, je suis à l'aise sur l'écosystème **.NET / Java / SQL** et sur le web (Next.js, React, Vue, Node).

> 📍 **Basé à Toulouse**, et disponible sur **Genève et l'ensemble du bassin lémanique jusqu'à Lausanne** — en remote comme sur site.

---

## 🧭 Lodestone — assistant de connaissances souverain pour entreprises

> *Les employés interrogent en langage naturel la base documentaire de leur organisation ; l'IA répond en citant systématiquement ses sources.*

![Rust](https://img.shields.io/badge/Rust-000000?style=flat&logo=rust&logoColor=white)
![Axum](https://img.shields.io/badge/Axum-000000?style=flat&logo=rust&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL%20%2B%20pgvector-4169E1?style=flat&logo=postgresql&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat&logo=ollama&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)

Les PME croulent sous la documentation interne (procédures, comptes-rendus, doc technique, contrats) et perdent un temps considérable à « savoir où c'est écrit ». Lodestone transforme ces documents épars en une mémoire d'entreprise interrogeable.

**Le parti pris : la souveraineté des données.** Là où les acteurs du marché envoient tout chez un fournisseur tiers, Lodestone peut faire tourner le LLM **en local (Ollama) ou sur l'infrastructure du client**. Les documents internes ne quittent jamais l'entreprise — un argument décisif pour les secteurs santé, juridique, finance et public.

**Ce que je construis :**

| Couche | Choix technique | Pourquoi |
|---|---|---|
| Backend | **Rust + Axum + Tokio** | Async natif, idéal pour le streaming WebSocket token par token |
| Persistance | **PostgreSQL + pgvector** (SeaORM) | Une seule base pour le relationnel *et* les vecteurs — zéro infra supplémentaire |
| IA | **Ollama** via une API OpenAI-compatible | Un unique client Rust derrière un trait `LlmClient` : basculer local ↔ cloud est une variable d'environnement |
| Frontend | **Next.js + Shadcn/ui + Tailwind** | SSR pour le marketing, WebSocket pour le chat temps réel |

**Points d'architecture que j'ai particulièrement travaillés :**

- 🔐 **Multi-tenant en schéma partagé** — isolation garantie par un filtrage systématique sur `org_id`, jusque dans la recherche vectorielle.
- 🧱 **Workspace Cargo multi-crates** — toute la logique pure (crypto, chunking, client LLM) sort en *library crates* testables hors-ligne ; le binaire ne garde que la glu web.
- 🛡️ **RBAC dans les extracteurs Axum** — `AuthUser` + `OrgMember { role }`, l'autorisation vit à la frontière HTTP, pas éparpillée dans les handlers.
- 🧪 **Qualité non négociable** — `clippy -D warnings`, jamais de `.unwrap()` en handler, tests d'intégration sur un Postgres+pgvector jetable (`testcontainers`) avec le LLM mocké derrière son trait.
- 📚 **RAG avec traçabilité** — chaque réponse persiste les fragments qui l'ont produite, avec leur score de similarité.

🚧 *Projet en cours de développement — dépôt bientôt public.*

---

## 🌟 Autres projets

### 🏃 [Sport Flow](https://github.com/Zolkn-Sama/m1-s2-web-projet) — application web full stack

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat&logo=spring&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)

Application web développée **en équipe de 4 en Master 1 MIAGE** et **déployée en production** sur [sportflow.linv.dev](https://sportflow.linv.dev).

Stack **Spring Boot + PostgreSQL** conteneurisée avec Docker Compose, et une **CI/CD complète sous GitHub Actions** : analyse SonarQube, couverture JaCoCo, publication de l'image sur GHCR, Javadoc et Swagger UI déployés automatiquement sur GitHub Pages. Le projet où la chaîne de livraison est allée le plus loin — du commit jusqu'au déploiement.

---

### 🏭 [m1-s2-indu](https://github.com/Zolkn-Sama/m1-s2-indu) — industrialisation du développement logiciel

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=openjdk&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat&logo=apachemaven&logoColor=white)
![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat&logo=sonarqube&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)

Projet **Java / Maven** mené à **6 en Master 1 MIAGE**, centré non pas sur la feature mais sur la **chaîne de production logicielle** : quality gate **SonarQube**, mesure de couverture, **Javadoc publiée**, et un workflow Git strict (branche dédiée → pull request → revue → aucun merge sans consentement).

C'est le projet qui m'a formé aux réflexes que j'applique aujourd'hui partout : la CI décide, pas les habitudes.

📊 [Javadoc](https://linventif.github.io/m1-s2-indu) · [Tableau de bord SonarQube](https://sorar.linv.dev)

---

### 🩺 [R6.06-GestionRDV](https://github.com/Zolkn-Sama/R6.06-GestionRDV-main) — gestion de rendez-vous médicaux

![.NET](https://img.shields.io/badge/.NET%206-512BD4?style=flat&logo=dotnet&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=flat&logo=csharp&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)

Application de **gestion de rendez-vous pour un cabinet médical**, construite en trois blocs séparés : une **API .NET 6** (`Sae.MediPlan.Api`), sa **suite de tests** (`Sae.MediPlan.ApiTests`) et une **SPA** cliente (`Sae.MediPlan.Spa`).

Au menu : **PostgreSQL conteneurisé** via Docker Compose, migrations **EF Core**, authentification **JWT** avec secrets sortis du code (`dotnet user-secrets`), et un **MCD** modélisé en PlantUML. Le dépôt embarque aussi une base `legacy/`, ce qui en fait autant un exercice de reprise d'existant que de développement neuf.

---

### ⚡ SAÉ 4.01 — configurateur de véhicules Tesla *(API .NET + client Vue)*

![.NET](https://img.shields.io/badge/ASP.NET%20Core%206-512BD4?style=flat&logo=dotnet&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=flat&logo=csharp&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=flat&logo=vue.js&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=flat&logo=swagger&logoColor=black)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat&logo=microsoftazure&logoColor=white)

Projet **full stack en deux dépôts** (BUT Informatique, IUT d'Annecy) : un configurateur de véhicules type Tesla couvrant le catalogue — modèles, motorisations, variantes, options, accessoires — jusqu'au tunnel de commande, comptes clients et moyens de paiement inclus.

- 🔌 **[API-Tesla](https://github.com/Zolkn-Sama/API-Tesla-main)** — API REST **ASP.NET Core 6** sur **EF Core + PostgreSQL**, en **architecture en couches avec inversion de dépendance** : les 22 contrôleurs ne connaissent jamais le `DbContext`, seulement des interfaces `IDataRepository<T>` injectées au démarrage. Authentification **JWT** (HMAC-SHA256, validation stricte émetteur/audience/signature, `ClockSkew` à zéro) avec politiques *Admin* / *User*. Documentation **Swagger/OpenAPI** générée depuis les annotations `[ProducesResponseType]`. Chaque contrôleur est testé **en double : sur base réelle et sur repository mocké (Moq)** — c'est précisément ce que l'abstraction repository achète. Déploiement continu sur **Azure App Service** via GitHub Actions.
- 🖥️ **[Client_Tesla](https://github.com/Zolkn-Sama/SAE4.01-Client_Tesla)** — **SPA Vue.js** consommant l'API, développée à plusieurs sur une centaine de commits.

---

## 🛠️ Stack & outils

**Langages**

![Rust](https://img.shields.io/badge/Rust-000000?style=flat&logo=rust&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=flat&logo=csharp&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)

**Frameworks & libs**

![Axum](https://img.shields.io/badge/Axum-000000?style=flat&logo=rust&logoColor=white)
![Tokio](https://img.shields.io/badge/Tokio-000000?style=flat&logo=rust&logoColor=white)
![.NET](https://img.shields.io/badge/.NET-512BD4?style=flat&logo=dotnet&logoColor=white)
![Blazor](https://img.shields.io/badge/Blazor-512BD4?style=flat&logo=blazor&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat&logo=spring&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=flat&logo=vue.js&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)

**Outils & DevOps**

![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![GitLab](https://img.shields.io/badge/GitLab-FC6D26?style=flat&logo=gitlab&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat&logo=sonarqube&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat&logo=microsoftazure&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)

---

## 🎓 Parcours

| Période | Formation / Expérience |
|---|---|
| **2025 – 2027** | Master MIAGE — *UT1 Capitole, Toulouse* |
| **2024** | Stage **Groupe-Entis** — appli compta full stack (C# / .NET / Blazor / API REST) |
| **2023** | Stage **ELDORA (Suisse)** — développement d'une **marketplace interne** (React / SPFx / Azure / MS Graph) |
| **2021 – 2024** | BUT Informatique — *IUT Annecy* |

---

## 📫 Me contacter

- 📧 **Email** — <enzo.landrecy@gmail.com>
- 💼 **LinkedIn** — [linkedin.com/in/enzo-landrecy](https://www.linkedin.com/in/enzo-landrecy)
- 📍 **Toulouse, France** — et disponible sur **Genève / bassin lémanique jusqu'à Lausanne**
- 🌐 Remote ou sur site

<p align="center"><i>Merci d'être passé 👋</i></p>
