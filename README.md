# **_Risques liés à l'utilisation d'une IA pour coder (version très détaillée et exhaustive)_**

Ce document rassemble l’ensemble des risques connus, directs et indirects, liés à l’usage d’une [**intelligence artificielle générative**](https://www.google.com/search?q=intelligence+artificielle+g%C3%A9n%C3%A9rative) pour la production de code.  
Il couvre les aspects techniques, humains, organisationnels, juridiques et sécuritaires.  
Même si l’IA peut accélérer le développement, elle introduit des vulnérabilités et des dépendances risquées.  
La qualité du code, la sécurité et la maintenabilité sont directement impactées.  
Une vigilance humaine est indispensable pour éviter des erreurs critiques et des failles de sécurité.

**Sources :**  
- [OpenAI Safety Best Practices](https://platform.openai.com/docs/guides/safety)  
- [Wikipedia – Generative AI](https://en.wikipedia.org/wiki/Generative_artificial_intelligence)

---

## 1. Risques techniques

### 1.1 Bugs subtils et erreurs logiques
L’IA peut générer du code qui semble correct mais ne respecte pas parfaitement les [**spécifications fonctionnelles**](https://www.google.com/search?q=sp%C3%A9cifications+fonctionnelles).  
Elle peut omettre des cas limites (données [**null**](https://www.google.com/search?q=null), dépassements, données [**corrompues**](https://www.google.com/search?q=donn%C3%A9es+corrompues)) et produire des [**erreurs logiques**](https://www.google.com/search?q=erreurs+logiques) difficiles à repérer.  
Le code peut réutiliser des [**approches obsolètes**](https://www.google.com/search?q=approches+obsol%C3%A8tes) et générer des comportements [**imprévus en production**](https://www.google.com/search?q=impr%C3%A9visibles+en+production).  
Sans revue humaine, ces erreurs peuvent se propager dans le système entier, affectant d’autres modules.  
La supervision est donc essentielle pour identifier les incohérences introduites par l’IA.

**Sources :**  
- [AI-Generated Code Risks – ACM](https://dl.acm.org/doi/10.1145/3446871)  
- [Stack Overflow Developer Survey 2023](https://survey.stackoverflow.co/2023/)

---

### 1.2 Code non fonctionnel ou incomplet
Le code produit par l’IA peut :  
- ne pas [**compiler**](https://www.google.com/search?q=compiler),  
- dépendre de [**bibliothèques incompatibles**](https://www.google.com/search?q=biblioth%C3%A8ques+incompatibles),  
- être insuffisamment [**testé**](https://www.google.com/search?q=test%C3%A9),  
- reposer sur des [**suppositions incorrectes**](https://www.google.com/search?q=suppositions+incorrectes).  
Ces limitations provoquent des erreurs à l’exécution qui ne seraient pas visibles sans tests approfondis.

**Sources :**  
- [GitHub – Copilot Security Risks](https://docs.github.com/en/copilot/security-and-privacy)  
- [IEEE Software – AI in Development](https://ieeexplore.ieee.org/document/9523772)

---

### 1.3 Utilisation de mauvaises pratiques
L’IA peut générer :  
- des [**structures inefficaces**](https://www.google.com/search?q=structures+inefficaces),  
- des [**duplications de code**](https://www.google.com/search?q=duplications+de+code),  
- des [**patterns anti-architecture**](https://www.google.com/search?q=patterns+anti-architecture),  
- des solutions [**non idiomatiques**](https://www.google.com/search?q=non+idiomatiques).  
Ces pratiques compliquent la maintenance et augmentent la dette technique globale.  
Elles peuvent rendre le code vulnérable aux failles et difficiles à intégrer dans une architecture cohérente.

**Sources :**  
- [Refactoring Guru – Code Smells](https://refactoring.guru/smells)  
- [Martin Fowler – Software Architecture](https://martinfowler.com/)

---

### 1.4 Code non optimisé
L’IA peut générer du code qui :  
- consomme trop de [**mémoire**](https://www.google.com/search?q=m%C3%A9moire),  
- effectue des [**opérations inutiles**](https://www.google.com/search?q=op%C3%A9rations+inutiles),  
- adopte une [**complexité algorithmique excessive**](https://www.google.com/search?q=complexit%C3%A9+algorithmique+excessive),  
- ignore les [**optimisations natives du langage ou framework**](https://www.google.com/search?q=optimisations+langage+framework).  
Ces inefficacités peuvent ralentir l’application, accroître les coûts et exposer le système à des erreurs.  
La revue manuelle est donc indispensable.

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
Ces erreurs peuvent provoquer des incompatibilités et fragiliser l’ensemble du projet.  
L’IA ne vérifie pas les mises à jour ou la compatibilité des versions.

**Sources :**  
- [NPM Security Practices](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#dependencies)  
- [OWASP Dependency Check](https://owasp.org/www-project-dependency-check/)

---

### 1.6 Difficulté à maintenir le code généré
Sans [**commentaires pertinents**](https://www.google.com/search?q=commentaires+pertinents), le code devient difficile à comprendre et à [**déboguer**](https://www.google.com/search?q=d%C3%A9boguer).  
La mise à jour et la modification peuvent casser des modules critiques.  
L’IA peut introduire des incohérences dans l’architecture.  
Chaque modification nécessite un audit minutieux pour éviter des régressions.  
La maintenabilité devient un risque majeur pour tout projet à long terme.

**Sources :**  
- [Clean Code – Robert C. Martin](https://www.oreilly.com/library/view/clean-code-a/9780136083238/)  
- [IEEE Software – AI Maintainability](https://ieeexplore.ieee.org/document/9322333)

---

## 2. Risques liés à la sécurité

### 2.1 Vulnérabilités classiques non gérées
Le code IA peut contenir :  
- [**injections SQL**](https://owasp.org/www-community/attacks/SQL_Injection),  
- [**failles XSS**](https://owasp.org/www-community/attacks/xss/),  
- [**attaques CSRF**](https://owasp.org/www-community/attacks/csrf),  
- contournement d’authentification,  
- absence de [**validation des entrées**](https://owasp.org/www-project-top-ten/).  
Ces vulnérabilités exposent l’application à des attaques externes.  
L’IA ne détecte pas automatiquement les scénarios de sécurité critiques.  
Une supervision humaine est essentielle pour éviter les fuites de données.

**Sources :**  
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)  
- [Security Risks of AI-generated Code](https://dl.acm.org/doi/10.1145/3454122)

---

### 2.2 Mécanismes cryptographiques incorrects
L’IA peut utiliser sa propre [**cryptographie**](https://www.google.com/search?q=cryptographie) ou des méthodes [**obsolètes**](https://www.google.com/search?q=obsol%C3%A8tes+MD5+SHA1+RC4).  
Des [**clés faibles**](https://www.google.com/search?q=cl%C3%A9s+faibles) peuvent compromettre la sécurité.  
La gestion des [**secrets**](https://www.google.com/search?q=secrets) peut être incomplète ou incorrecte.  
Ces risques exposent l’ensemble du projet à des violations graves.  
L’IA ne garantit pas la conformité aux standards de sécurité.

**Sources :**  
- [OWASP Cryptographic Storage](https://owasp.org/www-project-top-ten/2017/A3_2017-Sensitive_Data_Exposure.html)  
- [NIST Cryptography Guidelines](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)

---

### 2.3 Manque de gestion d’erreurs sécurisée
Le code généré peut produire des [**exceptions non gérées**](https://www.google.com/search?q=exceptions+non+g%C3%A9r%C3%A9es) ou des logs contenant des [**données confidentielles**](https://www.google.com/search?q=donn%C3%A9es+confidentielles).  
Les messages d’erreur peuvent révéler des informations sensibles.  
Ces failles peuvent être exploitées pour des attaques ciblées.  
Sans supervision humaine, les risques restent élevés.  
L’IA n’assure pas une gestion robuste des erreurs critiques.

**Sources :**  
- [OWASP Logging Security](https://owasp.org/www-project-top-ten/2017/A6_2017-Security_Misconfiguration.html)  
- [IEEE – Error Handling in AI Systems](https://ieeexplore.ieee.org/document/9390012)

---

## 3. Risques humains
### 3.1 Dépendance excessive
Une utilisation massive de l’IA peut provoquer :  
- recul des [**compétences de base**](https://www.google.com/search?q=comp%C3%A9tences+de+base),  
- incapacité à coder sans assistance,  
- perte de compréhension approfondie du code.  
Cette dépendance crée des risques de mauvaise maintenance et de dette technique.  
L’IA peut donner une illusion de maîtrise, alors que les erreurs sont masquées.

**Sources :**  
- [ACM Digital Library – Human Factors in AI](https://dl.acm.org/doi/10.1145/3313831)  
- [Stack Overflow Developer Survey 2023](https://survey.stackoverflow.co/2023/)

---

### 3.2 Illusion de compétence
Le développeur peut croire comprendre le code généré,  
maîtriser une [**technologie**](https://www.google.com/search?q=technologie),  
ou avoir produit un code fiable, alors que l’essentiel provient de l’IA.  
Cette illusion peut entraîner des décisions incorrectes en production.  
Sans audits et revues, les risques augmentent rapidement.

**Sources :**  
- [Dunning-Kruger Effect in Programming](https://www.sciencedirect.com/science/article/pii/S0742051X21001436)

---

### 3.3 Manque de revues de code sérieuses
Les équipes peuvent valider du code :  
- sans relecture approfondie,  
- sous pression,  
- en supposant que “l’IA a raison”.  
Cette pratique accroît considérablement la [**dette technique**](https://www.google.com/search?q=dette+technique) et la vulnérabilité du projet.  
Chaque erreur ignorée peut se propager et créer des incidents critiques.

**Sources :**  
- [Martin Fowler – Technical Debt](https://martinfowler.com/bliki/TechnicalDebt.html)

---

## 4. Risques organisationnels

### 4.1 Perte de cohérence dans l’architecture
En utilisant l’IA pour différents modules :  
- les [**conventions de code**](https://www.google.com/search?q=conventions+de+code) varient,  
- les [**patterns**](https://www.google.com/search?q=patterns) deviennent incohérents,  
- la [**structure globale**](https://www.google.com/search?q=structure+globale) perd sa logique.  
Cette incohérence peut entraîner des bugs et des failles de sécurité.  
La supervision humaine est essentielle pour assurer l’homogénéité du projet.

**Sources :**  
- [IEEE Software – Software Architecture](https://ieeexplore.ieee.org/document/9032331)

---

### 4.2 Dégradation du workflow de développement
L’IA peut contourner les processus standard,  
générer du code sans respecter les [**guidelines internes**](https://www.google.com/search?q=guidelines+internes),  
ou ignorer les conventions de commits, pipelines CI et tests.  
Cette pratique augmente les risques d’erreurs non détectées.  
La productivité peut être compromise par des solutions instables.

**Sources :**  
- [Agile Alliance – Dev Workflow](https://www.agilealliance.org/glossary/devops/)

---

### 4.3 Faible reproductibilité
Le même prompt peut produire :  
- une version différente du code,  
- une solution incompatible,  
- une alternative non vérifiable.  
Cette variabilité accroît le risque d’incohérences et de bugs en production.  
Le contrôle humain reste indispensable.

**Sources :**  
- [ACM Transactions on Software Engineering – Reproducibility](https://dl.acm.org/doi/10.1145/3411764)

---

## 5. Risques juridiques

### 5.1 Propriété intellectuelle
Le code généré peut ressembler à du code sous licence restrictive,  
inclure des extraits protégés,  
ou enfreindre des obligations légales.  
Ces risques peuvent entraîner des sanctions et des litiges.  
L’utilisation d’IA nécessite une vigilance légale constante.

**Sources :**  
- [GitHub Copilot Licensing FAQ](https://docs.github.com/en/copilot/getting-started-with-github-copilot/about-github-copilot#licensing)

---

### 5.2 Incompatibilité de licences
L’IA peut proposer des dépendances sous :  
- GPL, AGPL, LGPL,  
- licences manipulant les conditions d'utilisation.  
Certaines licences peuvent être incompatibles avec des projets commerciaux.  
Le risque juridique augmente sans audit attentif.

**Sources :**  
- [Open Source Initiative – License Types](https://opensource.org/licenses)

---

### 5.3 Confidentialité et protection des données
Le code peut être envoyé sur des serveurs externes,  
contenir des [**données sensibles**](https://www.google.com/search?q=donn%C3%A9es+sensibles),  
ou intégrer par erreur des identifiants ou [**secrets**](https://www.google.com/search?q=secrets).  
Ces fuites peuvent compromettre la sécurité et la conformité légale.  
Une supervision stricte est nécessaire pour limiter ces risques.

**Sources :**  
- [GDPR Compliance Guide](https://gdpr.eu/)  
- [OpenAI Data Usage Policy](https://openai.com/policies/data-usage)

---

## 6. Risques stratégiques

### 6.1 Perte de maîtrise du produit
Si trop de code est généré automatiquement,  
le cœur du produit devient difficile à expliquer,  
la compréhension technique se perd,  
et la maintenance dépend fortement de l’outil.  
Ce risque peut compromettre l’évolution future du projet.

**Sources :**  
- [IEEE – Strategic Risks of AI](https://ieeexplore.ieee.org/document/9321122)

---

### 6.2 Risque de dépendance à un fournisseur
Selon l’IA utilisée :  
- évolutions imprévisibles du modèle,  
- coûts croissants,  
- limitations futures,  
- changements de politique d'utilisation.  
Cette dépendance peut fragiliser la stratégie de développement.

**Sources :**  
- [Vendor Lock-in Risks – ACM](https://dl.acm.org/doi/10.1145/3460172)

---

## 7. Risques pédagogiques (chez les débutants)

### 7.1 Apprentissage superficiel
L'utilisateur peut :  
- ne pas comprendre les bases du langage,  
- ignorer les [**structures de données**](https://www.google.com/search?q=structures+de+donn%C3%A9es),  
- ne pas savoir déboguer seul.  
Cette dépendance à l’IA ralentit la progression réelle et la compréhension approfondie.  
Les erreurs peuvent se répéter sans apprentissage correctif.

**Sources :**  
- [IEEE Transactions on Education](https://ieeexplore.ieee.org/document/9381001)

---

### 7.2 Mauvaise compréhension des erreurs
Les débutants ne peuvent pas toujours :  
- expliquer pourquoi le code ne marche pas,  
- corriger les bugs introduits,  
- comprendre l'approche théorique.  
Cela entraîne des habitudes de codage incorrectes et des risques de propagation des erreurs.

**Sources :**  
- [ACM Education Reports](https://dl.acm.org/doi/10.1145/3429789)

---

### 7.3 Mauvaises habitudes codifiées
Exemples :  
- copier-coller sans réflexion,  
- absence de tests,  
- dépendance aux prompts plutôt qu’à la logique.  
Ces pratiques augmentent les risques de bugs et de dette technique.

**Sources :**  
- [IEEE Software – Coding Practices](https://ieeexplore.ieee.org/document/9322211)

---

## 8. Risques liés à la gestion des prompts

### 8.1 Prompts mal formulés
Un prompt ambigu peut générer :  
- du code dangereux,  
- une mauvaise architecture,  
- des solutions incohérentes.  
La formulation des prompts devient un facteur critique de sécurité et fiabilité.

**Sources :**  
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompting)

---

### 8.2 Fuite de contexte
Fournir trop d’informations à l’IA peut provoquer :  
- divulgation de données sensibles,  
- surcharge contextuelle,  
- perte de contrôle sur les informations envoyées.  
Cette fuite peut compromettre la sécurité du projet.

**Sources :**  
- [AI Privacy Risks – IEEE](https://ieeexplore.ieee.org/document/9387763)

---

### 8.3 Hallucinations techniques
L’IA peut inventer :  
- des fonctions inexistantes,  
- des arguments incorrects,  
- des modules imaginaires,  
- des solutions théoriques mais irréalisables.  
Ces hallucinations introduisent des risques graves pour le code produit.

**Sources :**  
- [OpenAI – AI Hallucinations](https://platform.openai.com/docs/guides/gpt-best-practices)

---

## 9. Fonctionnement de l’IA et système de tokens

L’IA générative repose sur des [**modèles de langage**](https://www.google.com/search?q=mod%C3%A8les+de+langage) pré-entraînés sur de vastes corpus.  
Chaque mot ou fragment est converti en [**tokens**](https://www.google.com/search?q=tokens+NLP), unités numériques que le modèle traite.  
Le modèle prédit statistiquement le token suivant pour produire du code ou du texte.  
Des limites de tokens par requête existent, pouvant fragmenter la logique du code généré.  
Exemple pratique : [VittaScience – IA et tokens](https://fr.vittascience.com/ia/text?localId=loc644547c3726ac0).

**Sources :**  
- [OpenAI – How GPT Works](https://platform.openai.com/docs/guides/gpt-best-practices)  
- [VittaScience – IA Text Tokens](https://fr.vittascience.com/ia/text?localId=loc644547c3726ac0)

---

# Conclusion

L’usage d’une IA pour coder comporte des risques critiques :  
- sécurité,  
- bugs subtils,  
- dette technique,  
- mauvaise maintenabilité,  
- dépendance excessive,  
- vulnérabilités légales.  

Sans contrôle humain, tests rigoureux et audit, le code peut devenir inutilisable ou dangereux.  
L’IA doit être un **outil d’accélération**, pas un substitut au jugement humain.  
Une compréhension du système de tokens et des limites du modèle est essentielle pour anticiper les risques.

**Sources générales :**  
- [OpenAI Safety Best Practices](https://platform.openai.com/docs/guides/safety)  
- [ACM Digital Library – AI Risks](https://dl.acm.org/)  
- [IEEE Software – AI in Software Development](https://ieeexplore.ieee.org/)
