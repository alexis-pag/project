# **_Risques liés à l'utilisation d'une IA pour coder_**

Ce document rassemble l’ensemble des risques connus, directs et indirects, liés à l’usage d’une [**intelligence artificielle générative**](https://www.google.com/search?q=intelligence+artificielle+g%C3%A9n%C3%A9rative) pour la production de code.  
Il couvre les aspects techniques, humains, organisationnels, juridiques et sécuritaires.

**Sources :**  
- [OpenAI Safety Best Practices](https://platform.openai.com/docs/guides/safety)  
- [Wikipedia – Generative AI](https://en.wikipedia.org/wiki/Generative_artificial_intelligence)

---

## 1. Risques techniques

### 1.1 Bugs subtils et erreurs logiques
L’IA peut générer du code :  
- qui semble correct mais ne respecte pas parfaitement les [**spécifications fonctionnelles**](https://www.google.com/search?q=sp%C3%A9cifications+fonctionnelles),  
- qui omet des cas limites (données [**null**](https://www.google.com/search?q=null), dépassements, données [**corrompues**](https://www.google.com/search?q=donn%C3%A9es+corrompues)),  
- qui contient des [**erreurs logiques**](https://www.google.com/search?q=erreurs+logiques) difficiles à détecter,  
- qui réutilise des [**approches obsolètes**](https://www.google.com/search?q=approches+obsol%C3%A8tes),  
- qui produit des comportements [**imprévus en production**](https://www.google.com/search?q=impr%C3%A9visibles+en+production).  

**Pourquoi ?** L’IA n’exécute pas le code, elle anticipe statistiquement ce qui “semble correct”.  

**Sources :**  
- [AI-Generated Code Risks – ACM](https://dl.acm.org/doi/10.1145/3446871)  
- [Stack Overflow Developer Survey 2023](https://survey.stackoverflow.co/2023/)

---

### 1.2 Code non fonctionnel ou incomplet
Le code produit peut :  
- ne pas [**compiler**](https://www.google.com/search?q=compiler),  
- dépendre de [**bibliothèques incompatibles**](https://www.google.com/search?q=biblioth%C3%A8ques+incompatibles),  
- être insuffisamment [**testé**](https://www.google.com/search?q=test%C3%A9),  
- reposer sur des [**suppositions incorrectes**](https://www.google.com/search?q=suppositions+incorrectes).  
L’IA n’a pas accès à la même vision que l’environnement réel (fichiers, architecture, erreurs compilateur).  
Il est essentiel de vérifier manuellement chaque génération pour éviter des comportements inattendus.  

**Sources :**  
- [GitHub – Copilot Security Risks](https://docs.github.com/en/copilot/security-and-privacy)  
- [IEEE Software – AI in Development](https://ieeexplore.ieee.org/document/9523772)

---

### 1.3 Utilisation de mauvaises pratiques
L’IA peut produire :  
- des [**structures inefficaces**](https://www.google.com/search?q=structures+inefficaces),  
- des [**duplications de code**](https://www.google.com/search?q=duplications+de+code),  
- des [**patterns anti-architecture**](https://www.google.com/search?q=patterns+anti-architecture) (god objects, couplage excessif),  
- des solutions [**non idiomatiques**](https://www.google.com/search?q=non+idiomatiques).  
Ces mauvaises pratiques entraînent une [**dette technique**](https://www.google.com/search?q=dette+technique) et compliquent la maintenance.  
L’intégration dans des systèmes existants peut générer des incohérences et des anomalies de performance.  

**Sources :**  
- [Refactoring Guru – Code Smells](https://refactoring.guru/smells)  
- [Martin Fowler – Software Architecture](https://martinfowler.com/)

---

### 1.4 Code non optimisé
L'IA peut générer du code qui :  
- consomme plus de [**mémoire**](https://www.google.com/search?q=m%C3%A9moire),  
- effectue des [**opérations inutiles**](https://www.google.com/search?q=op%C3%A9rations+inutiles),  
- adopte une [**complexité algorithmique excessive**](https://www.google.com/search?q=complexit%C3%A9+algorithmique+excessive),  
- ne profite pas des [**optimisations natives du langage ou framework**](https://www.google.com/search?q=optimisations+langage+framework).  
Ces problèmes dégradent les [**performances**](https://www.google.com/search?q=performances) et augmentent la latence perçue par l’utilisateur.  
Un contrôle manuel et des tests de performance restent indispensables.  

**Sources :**  
- [Big-O Complexity](https://en.wikipedia.org/wiki/Big_O_notation)  
- [High Performance JavaScript](https://www.oreilly.com/library/view/high-performance-javascript/9780596802798/)

---

### 1.5 Génération de dépendances incompatibles
Le code généré peut :  
- installer des versions [**instables**](https://www.google.com/search?q=instables),  
- mélanger des versions [**incompatibles**](https://www.google.com/search?q=incompatibles),  
- utiliser des [**bibliothèques non maintenues**](https://www.google.com/search?q=biblioth%C3%A8ques+non+maintenues),  
- faire appel à des [**API dépréciées**](https://www.google.com/search?q=API+d%C3%A9pr%C3%A9ci%C3%A9es).  
Ces incompatibilités peuvent générer des erreurs à l’exécution et compromettre la sécurité.  
Un audit régulier des dépendances est indispensable.  

**Sources :**  
- [NPM Security Practices](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#dependencies)  
- [OWASP Dependency Check](https://owasp.org/www-project-dependency-check/)

---

### 1.6 Difficulté à maintenir le code généré
Sans [**commentaires pertinents**](https://www.google.com/search?q=commentaires+pertinents), il devient difficile de :  
- comprendre l’intention originale,  
- [**déboguer**](https://www.google.com/search?q=d%C3%A9boguer),  
- mettre à jour,  
- modifier sans casser l’existant.  
Le manque de documentation claire augmente les risques d’erreurs et la complexité des interventions.  
Des conventions de commentaires et des revues régulières sont essentielles.  

**Sources :**  
- [Clean Code – Robert C. Martin](https://www.oreilly.com/library/view/clean-code-a/9780136083238/)  
- [IEEE Software – AI Maintainability](https://ieeexplore.ieee.org/document/9322333)

---

## 2. Risques liés à la sécurité

### 2.1 Vulnérabilités classiques non gérées
Le code généré peut laisser passer :  
- [**injections SQL**](https://owasp.org/www-community/attacks/SQL_Injection),  
- [**failles XSS**](https://owasp.org/www-community/attacks/xss/),  
- [**attaques CSRF**](https://owasp.org/www-community/attacks/csrf),  
- contournement d’authentification,  
- absence de [**validation des entrées**](https://owasp.org/www-project-top-ten/).  
Ces vulnérabilités peuvent être exploitées par des attaquants pour accéder à des données sensibles.  
La vérification manuelle et les tests de sécurité sont obligatoires.  

**Sources :**  
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)  
- [Security Risks of AI-generated Code](https://dl.acm.org/doi/10.1145/3454122)

---

### 2.2 Mécanismes cryptographiques incorrects
L’IA peut :  
- implémenter sa propre [**cryptographie**](https://www.google.com/search?q=cryptographie),  
- utiliser des fonctions [**obsolètes**](https://www.google.com/search?q=obsol%C3%A8tes+MD5+SHA1+RC4),  
- générer des [**clés faibles**](https://www.google.com/search?q=cl%C3%A9s+faibles),  
- mal gérer les [**secrets**](https://www.google.com/search?q=secrets).  
Ces erreurs compromettent la confidentialité et la sécurité des systèmes.  
Les protocoles cryptographiques standard doivent toujours être utilisés.  

**Sources :**  
- [OWASP Cryptographic Storage](https://owasp.org/www-project-top-ten/2017/A3_2017-Sensitive_Data_Exposure.html)  
- [NIST Cryptography Guidelines](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)

---

### 2.3 Manque de gestion d’erreurs sécurisée
L’IA peut produire :  
- des messages d’erreur exposant des informations sensibles,  
- des [**exceptions non gérées**](https://www.google.com/search?q=exceptions+non+g%C3%A9r%C3%A9es),  
- des logs contenant des [**données confidentielles**](https://www.google.com/search?q=donn%C3%A9es+confidentielles).  
Cela peut faciliter l’exploitation de vulnérabilités ou compromettre la confidentialité.  
Une gestion rigoureuse des erreurs et des logs est essentielle.  

**Sources :**  
- [OWASP Logging Security](https://owasp.org/www-project-top-ten/2017/A6_2017-Security_Misconfiguration.html)  
- [IEEE – Error Handling in AI Systems](https://ieeexplore.ieee.org/document/9390012)

---

## 3. Risques humains

### 3.1 Dépendance excessive
Une utilisation massive de l’IA peut provoquer un recul des [**compétences fondamentales**](https://www.google.com/search?q=comp%C3%A9tences+fondamentales) du développeur, réduisant sa capacité à coder sans assistance.  
Les développeurs risquent de perdre la compréhension des bases des langages ou des algorithmes essentiels.  
Cette dépendance peut créer un [**effet d’illusion de compétence**](https://www.google.com/search?q=illusion+de+comp%C3%A9tence), où l’utilisateur croit maîtriser le code alors qu’il se limite à le reproduire.  
Le recul des compétences entraîne aussi une diminution de la capacité à corriger des bugs complexes ou à comprendre les performances globales de l’application.  
Il devient indispensable d’accompagner l’usage d’IA par une formation continue et des revues de code rigoureuses.

**Sources :**  
- [ACM Digital Library – Human Factors in AI](https://dl.acm.org/doi/10.1145/3313831)  
- [Stack Overflow Developer Survey 2023](https://survey.stackoverflow.co/2023/)

---

### 3.2 Illusion de compétence
Le développeur peut croire qu’il comprend parfaitement le code généré par l’IA.  
Il peut surestimer sa maîtrise d’une [**technologie complexe**](https://www.google.com/search?q=technologie+complexe) ou d’un framework.  
Cette confiance excessive entraîne parfois des déploiements risqués sans vérifications approfondies.  
Les erreurs subtiles du code peuvent rester non détectées, fragilisant la qualité et la sécurité du logiciel.  
L’illusion de compétence accentue la dépendance à l’IA et complique l’apprentissage autonome.

**Sources :**  
- [Dunning-Kruger Effect in Programming](https://www.sciencedirect.com/science/article/pii/S0742051X21001436)

---

### 3.3 Manque de revues de code sérieuses
Certaines équipes se fient entièrement à l’IA pour la qualité du code.  
Les [**revues de code**](https://www.google.com/search?q=revues+de+code) sont alors superficielles ou inexistantes, augmentant le risque de bugs et de dette technique.  
La pression pour livrer rapidement accentue cette tendance, avec des correctifs souvent superficiels.  
Les erreurs logiques, incohérences et vulnérabilités passent inaperçues, fragilisant le projet.  
L’IA doit être intégrée comme un outil d’assistance, pas comme un substitut aux revues humaines.

**Sources :**  
- [Martin Fowler – Technical Debt](https://martinfowler.com/bliki/TechnicalDebt.html)

---

## 4. Risques organisationnels

### 4.1 Perte de cohérence dans l’architecture
L’utilisation d’IA pour produire différents modules peut générer des [**conventions de code**](https://www.google.com/search?q=conventions+de+code) variables et incohérentes.  
Les [**patterns**](https://www.google.com/search?q=patterns) architecturaux ne sont pas uniformément respectés, rendant la compréhension globale difficile.  
La [**structure globale**](https://www.google.com/search?q=structure+globale) du projet peut perdre sa logique initiale, compliquant l’intégration et la maintenance.  
Des modules isolés peuvent fonctionner indépendamment mais échouer lors de l’assemblage.  
Une gouvernance stricte et des guidelines internes sont essentielles pour limiter ces risques.

**Sources :**  
- [IEEE Software – Software Architecture](https://ieeexplore.ieee.org/document/9032331)

---

### 4.2 Dégradation du workflow de développement
L’IA peut contourner les processus standard et ignorer les [**guidelines internes**](https://www.google.com/search?q=guidelines+internes).  
Les conventions de commits, pipelines CI/CD et tests automatisés peuvent être contournés.  
Le flux de développement devient moins prévisible et plus difficile à auditer.  
Les équipes perdent en traçabilité et en contrôle sur les livrables.  
Il est crucial de définir des règles d’usage de l’IA dans le workflow pour maintenir la qualité.

**Sources :**  
- [Agile Alliance – Dev Workflow](https://www.agilealliance.org/glossary/devops/)

---

### 4.3 Faible reproductibilité
Le même prompt peut produire des résultats différents à chaque exécution.  
Une version du code peut être incompatible avec une autre ou contenir des erreurs uniques.  
L’IA ne garantit pas de [**reproductibilité**](https://www.google.com/search?q=reproductibilit%C3%A9) des solutions, compliquant les tests et l’audit.  
Cela rend la vérification et la maintenance du code plus complexes et chronophages.  
Des systèmes de versioning stricts et des tests automatisés sont nécessaires pour limiter l’impact.

**Sources :**  
- [ACM Transactions on Software Engineering – Reproducibility](https://dl.acm.org/doi/10.1145/3411764)

---

## 5. Risques juridiques

### 5.1 Propriété intellectuelle
Le code généré peut ressembler à du code protégé par des licences restrictives.  
Il peut inclure des extraits soumis à des droits d’auteur ou à des obligations contractuelles.  
Cela pose des risques de [**litiges**](https://www.google.com/search?q=litiges+propri%C3%A9t%C3%A9+intellectuelle) et de sanctions légales.  
L’utilisation de code généré automatiquement doit toujours vérifier la conformité avec les licences.  
Une politique interne et un audit régulier sont indispensables.

**Sources :**  
- [GitHub Copilot Licensing FAQ](https://docs.github.com/en/copilot/getting-started-with-github-copilot/about-github-copilot#licensing)

---

### 5.2 Incompatibilité de licences
Certaines dépendances proposées par l’IA peuvent être sous GPL, AGPL ou LGPL.  
Ces licences imposent des obligations pouvant être incompatibles avec un projet commercial.  
L’IA peut proposer du code [**contradictoire**](https://www.google.com/search?q=contradictoire+licences) avec la politique de l’entreprise.  
Il est nécessaire d’auditer toutes les bibliothèques utilisées pour éviter des risques juridiques.  
Les équipes doivent sensibiliser les développeurs à la gestion des licences open source.

**Sources :**  
- [Open Source Initiative – License Types](https://opensource.org/licenses)

---

### 5.3 Confidentialité et protection des données
Le code généré peut contenir des [**données sensibles**](https://www.google.com/search?q=donn%C3%A9es+sensibles).  
Des identifiants ou des [**secrets**](https://www.google.com/search?q=secrets) peuvent être accidentellement inclus.  
L’envoi automatique de code sur des serveurs externes peut exposer des informations confidentielles.  
Il est indispensable de mettre en place des politiques de sécurité et de conformité au RGPD.  
La supervision humaine reste essentielle pour éviter les fuites de données.

**Sources :**  
- [GDPR Compliance Guide](https://gdpr.eu/)  
- [OpenAI Data Usage Policy](https://openai.com/policies/data-usage)

---

## 6. Risques stratégiques

### 6.1 Perte de maîtrise du produit
Si trop de code est généré automatiquement, le [**cœur du produit**](https://www.google.com/search?q=c%C5%93ur+du+produit) devient difficile à expliquer aux équipes et aux parties prenantes.  
La compréhension technique globale peut se perdre, rendant les décisions stratégiques plus risquées.  
La maintenance et les évolutions du projet dépendent fortement de l’outil d’IA utilisé, créant une forme de dépendance technologique.  
Le contrôle humain doit rester prioritaire pour garantir la cohérence et la qualité du produit.  
Les équipes doivent documenter et superviser chaque génération automatique pour éviter des surprises à long terme.

**Sources :**  
- [IEEE – Strategic Risks of AI](https://ieeexplore.ieee.org/document/9321122)

---

### 6.2 Risque de dépendance à un fournisseur
En fonction de l’IA choisie, les évolutions du modèle peuvent être imprévisibles.  
Des [**coûts croissants**](https://www.google.com/search?q=co%C3%BBts+croissants) ou des limitations futures peuvent apparaître sans préavis.  
Les changements de politique d’utilisation peuvent restreindre l’accès ou modifier la licence du produit.  
Cette dépendance réduit la flexibilité de l’entreprise et peut bloquer l’innovation.  
Des stratégies de mitigation incluent le multi-fournisseur, le code open source et la formation interne.

**Sources :**  
- [Vendor Lock-in Risks – ACM](https://dl.acm.org/doi/10.1145/3460172)

---

## 7. Risques pédagogiques (chez les débutants)

### 7.1 Apprentissage superficiel
Les débutants peuvent se contenter de copier le code généré par l’IA sans comprendre les concepts sous-jacents.  
Ils risquent de ne pas maîtriser les [**structures de données**](https://www.google.com/search?q=structures+de+donn%C3%A9es) ni les algorithmes fondamentaux.  
Le développement de compétences logiques et analytiques est limité, freinant l’évolution professionnelle.  
Sans supervision, cette dépendance à l’IA peut conduire à des habitudes de programmation dangereuses.  
Les enseignants et mentors doivent intégrer l’IA comme outil pédagogique et non comme substitut de l’apprentissage actif.

**Sources :**  
- [IEEE Transactions on Education](https://ieeexplore.ieee.org/document/9381001)

---

### 7.2 Mauvaise compréhension des erreurs
Les débutants ne peuvent pas toujours identifier pourquoi un code ne fonctionne pas correctement.  
Ils peuvent être incapables de corriger des [**bugs complexes**](https://www.google.com/search?q=bugs+complexes) introduits par l’IA.  
La compréhension théorique et la capacité de débogage restent limitées.  
Le manque de raisonnement derrière le code généré fragilise l’apprentissage pratique.  
Une combinaison de formation et de supervision est indispensable pour éviter ces lacunes.

**Sources :**  
- [ACM Education Reports](https://dl.acm.org/doi/10.1145/3429789)

---

### 7.3 Mauvaises habitudes codifiées
Les utilisateurs peuvent développer des habitudes nocives comme : copier-coller sans réfléchir, ignorer les tests, ou dépendre exclusivement des prompts.  
Ces comportements réduisent la capacité d’analyse critique et la compréhension réelle des solutions.  
La [**dépendance aux prompts**](https://www.google.com/search?q=d%C3%A9pendance+aux+prompts) peut masquer l’absence de logique dans le code.  
Les projets deviennent alors plus fragiles et difficiles à maintenir.  
L’encadrement pédagogique et l’application de bonnes pratiques restent essentiels.

**Sources :**  
- [IEEE Software – Coding Practices](https://ieeexplore.ieee.org/document/9322211)

---

## 8. Risques liés à la gestion des prompts

### 8.1 Prompts mal formulés
Un prompt ambigu ou imprécis peut générer du code dangereux, incohérent ou inadapté à l’architecture.  
Les [**erreurs d’interprétation**](https://www.google.com/search?q=erreurs+d%27interpr%C3%A9tation) par l’IA peuvent produire des comportements imprévisibles.  
Une mauvaise formulation empêche de vérifier la conformité et la sécurité du code.  
Les prompts doivent être soigneusement conçus pour éviter des résultats inattendus.  
Le contrôle humain reste primordial pour valider chaque génération.

**Sources :**  
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompting)

---

### 8.2 Fuite de contexte
Si l’IA reçoit trop d’informations, il existe un risque de divulgation involontaire.  
La [**surcharge contextuelle**](https://www.google.com/search?q=surcharge+contextuelle) peut entraîner des réponses erronées ou des fuites de données sensibles.  
Le contrôle sur ce qui a été envoyé est limité, compromettant la sécurité.  
Des pratiques de minimisation des données et de vérification sont essentielles.  
Les équipes doivent former les utilisateurs à la gestion sûre des prompts.

**Sources :**  
- [AI Privacy Risks – IEEE](https://ieeexplore.ieee.org/document/9387763)

---

### 8.3 Hallucinations techniques
L’IA peut inventer des fonctions inexistantes, des arguments erronés ou des modules fictifs.  
Ces [**hallucinations techniques**](https://www.google.com/search?q=hallucinations+techniques) peuvent compromettre la fiabilité du projet.  
Les solutions théoriques proposées peuvent être techniquement impossibles à implémenter.  
La validation humaine et les tests unitaires sont indispensables pour vérifier la faisabilité.  
Comprendre les limites de l’IA permet d’éviter des erreurs critiques en production.

**Sources :**  
- [OpenAI – AI Hallucinations](https://platform.openai.com/docs/guides/gpt-best-practices)

---

# Conclusion

Utiliser une IA pour coder est extrêmement puissant, mais comporte des risques lourds s’il n’y a pas :  

- un contrôle humain systématique,  
- des tests rigoureux,  
- un audit de sécurité régulier,  
- la vérification de compatibilité et de cohérence architecturale,  
- des lignes directrices claires pour l’usage des prompts,  
- une maturité et une formation adaptées pour les utilisateurs.  

L’IA doit rester un accélérateur de productivité et non un substitut au jugement humain.  
Le suivi des bonnes pratiques, la supervision et la documentation rigoureuse sont essentiels pour limiter les risques.

**Sources générales :**  
- [OpenAI Safety Best Practices](https://platform.openai.com/docs/guides/safety)  
- [ACM Digital Library – AI Risks](https://dl.acm.org/)  
- [IEEE Software – AI in Software Development](https://ieeexplore.ieee.org/)
