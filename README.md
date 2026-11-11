# Projet Web Distribuees — Architecture Microservices

Equipe de **6 membres** — **6 microservices metier** (Spring Boot, 1 par membre) + **1 module commun : WellNest AI Engine** (Python ou Node.js, voir [MS7/README.md](MS7/README.md)).

> L'infrastructure (Eureka Server, API Gateway, Keycloak) sera ajoutee dans une etape ulterieure.

| Module        | Port | Base MySQL | Responsable    |
|---------------|------|------------|----------------|
| MS1           | 8081 | ms1_db     | Membre 1       |
| MS2           | 8082 | ms2_db     | Membre 2       |
| MS3           | 8083 | ms3_db     | Membre 3       |
| MS4           | 8084 | ms4_db     | Membre 4       |
| MS5           | 8085 | ms5_db     | Membre 5       |
| MS6           | 8086 | ms6_db     | Membre 6       |
| MS7 AI Engine | 8087 | -          | toute l'equipe |



## Structure d'un microservice Spring Boot (MS1 a MS6)

```
tn.esprit.msX
├── client       # appels vers les autres MS (ex: le MS commun)
├── config       # SecurityConfig, OpenAPI, etc.
├── controller   # REST controllers
├── dto          # objets d'echange (ne jamais exposer les entites)
├── entity       # entites JPA
├── exception    # exceptions + @RestControllerAdvice
├── mapper       # conversions entity <-> dto
├── repository   # Spring Data JPA
└── service      # logique metier
```

## Demarrage

1. MySQL sur `localhost:3306` (user `root`, mot de passe vide — a adapter dans `application.properties`).
   Chaque base `msX_db` est creee automatiquement.
2. Lancer le microservice :

```bash
cd MS1 && ./mvnw spring-boot:run
```

Swagger : `http://localhost:808X/swagger-ui.html`

## Tests

Les tests utilisent une base **H2 en memoire** (`src/test/resources/application.properties`),
donc `./mvnw test` fonctionne sans MySQL.

## Convention Git

- `master` : branche stable, pas de push direct
- une branche par membre / fonctionnalite : `feature/ms3-gestion-xxx`
- Pull Request + relecture par un autre membre avant merge
- Chacun ne modifie **que son dossier MSx** ; les changements sur le module commun (`MS7`, AI Engine) se font en concertation.
- Le contrat d'echange avec l'AI Engine (format commun) est defini dans `MS7/README.md`.
