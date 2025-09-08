# Document d’architecture

## Choix et justification de l’architecture de l’application  

### Architecture proposée :  
**Architecture en couches (Layered Architecture) avec API REST**

Pour répondre aux exigences de Knesh, nous proposons une architecture en couches moderne structurée ainsi :

#### Frontend (Angular)
- **Couche Présentation** : Composants Angular et templates  
- **Couche Service** : Services Angular et gestion d'état  
- **Couche Communication** : HTTP Client et intercepteurs  

#### Backend (Spring Boot)
- **Couche Présentation** : Controllers REST (`@RestController`)  
- **Couche Logique Métier** : Services métier (`@Service`)  
- **Couche Accès aux Données** : Repositories (`@Repository`)  
- **Couche Persistance** : Entités JPA et base de données  

### Justification technique
- **Rapide & économique** : standards Angular/Spring, MVP sans la complexité des microservices.  
- **Fiable & maintenable** : responsabilités claires, tests par couche, caches/health checks.  
- **Évolutive** : monolithe modulaire prêt pour messaging/recherche ou un découpage ultérieur.  

---

## 2. Choix et justification des librairies  

### 2.1 Librairies de test  

#### Front-end
- **Jasmine + Karma** (intégrés par défaut dans Angular)  
  - Jasmine : écriture des tests unitaires avec une syntaxe claire et expressive  
  - Karma : test runner pour l'exécution des tests dans différents navigateurs  
  - *Justification* : standards de l'écosystème Angular, parfaitement intégrés et documentés  

- **Cypress** pour les tests end-to-end  
  - Framework moderne de test E2E avec interface graphique intuitive  
  - Debugging facilité et captures d'écran automatiques en cas d'échec  
  - *Justification* : répond au besoin de rapidité avec des tests fiables et faciles à maintenir  

#### Back-end
- **JUnit 5** pour les tests unitaires  
  - Framework de test Java standard et mature  
  - Annotations riches et assertions puissantes  
  - *Justification* : standard de l'industrie, parfaitement documenté et évolutif  

- **Spring Boot Test + TestContainers**  
  - Spring Boot Test : tests d'intégration par couche  
  - TestContainers : tests avec base de données réelle en conteneur  
  - *Justification* : s'intègre parfaitement à l'architecture en couches, permettant de tester chaque niveau indépendamment  

---

### 2.2 Librairie de composants visuels  

- **Angular Material**  
  - Implémentation officielle du Material Design pour Angular  
  - Composants pré-construits (boutons, formulaires, navigation, etc.)  
  - Accessibilité intégrée (ARIA) et responsive design  
  - *Justification* : réduction des coûts grâce à des composants existants de qualité  

- **PrimeNG** (alternative/complément)  
  - Suite complète de composants UI riches pour Angular  
  - Composants spécialisés pour l'e-commerce (DataTable, Carousel, etc.)  
  - *Justification* : composants métier prêts à l'emploi, réduction significative du temps de développement grâce à la couche présentation pré-construite  

---

## 3. Choix et justification des paradigmes de programmation  

### Front-end
- **Programmation orientée objet** → TypeScript (interfaces, classes)  
- **Réactif (RxJS)** → Gestion élégante des flux de données  
- **Déclaratif & composantiel** → Templates déclaratifs et data-binding pour lisibilité  

*Justification* : plus simple à maintenir, plus rapide, et prêt pour faire évoluer l’UI sans tout casser.  

### Back-end
- **Paradigme Orienté Objet avec Architecture en Couches**  
  - OOP : Modélisation naturelle du domaine métier  
  - Programmation déclarative → Annotations Spring (`@Controller`, `@Service`, `@Repository`)  

*Justification* : clair pour les cas d’usage, rapide à développer, sûr et testable, prêt à évoluer.  
