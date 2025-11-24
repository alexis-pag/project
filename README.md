# **_Risques liés à l'utilisation d'une IA pour coder (version très détaillée et exhaustive)_**

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

**Sources :**  
- [OWASP Cryptographic Storage](https://owasp.org/www-project-top-ten/2017/A3_2017-Sensitive_Data_Exposure.html)  
- [NIST Cryptography Guidelines](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)

---

### 2.3 Manque de gestion d’erreurs sécurisée
Le code généré peut produire des messages d’erreur exposant des informations sensibles.  
Des [**exceptions non gérées**](https://www.google.com/search?q=exceptions+non+g%C3%A9r%C3%A9es) peuvent provoquer des plantages, tandis que les logs peuvent contenir des [**données confidentielles**](https://www.google.com/search?q=donn%C3%A9es+confidentielles).  
Ces comportements peuvent compromettre la sécurité du système et faciliter l’exploitation par des attaquants.  
L’IA ne sait pas toujours distinguer ce qui est critique, ce qui impose un contrôle humain systématique.  
Une stratégie de gestion d’erreurs robuste est donc indispensable pour éviter les failles introduites par le code généré.

**Sources :**  
- [OWASP Logging Security](https://owasp.org/www-project-top-ten/2017/A6_2017-Security_Misconfiguration.html)  
- [IEEE – Error Handling in AI Systems](https://ieeexplore.ieee.org/document/9390012)

---

### 2.4 Appels réseau non sécurisés
Le code produit peut utiliser HTTP au lieu de HTTPS, ne pas vérifier les certificats ou exposer des endpoints internes.  
Une mauvaise gestion des timeouts et des retries peut également provoquer des interruptions ou des comportements imprévisibles.  
Ces erreurs exposent le projet à des vulnérabilités réseau exploitables par des attaquants.  
L’IA n’a pas de compréhension intrinsèque des bonnes pratiques en sécurité réseau.  
Un audit humain reste indispensable pour s’assurer que les communications sont sécurisées et fiables.

**Sources :**  
- [OWASP Secure Communication](https://owasp.org/www-project-top-ten/)  
- [IEEE – Network Security in AI-generated Code](https://ieeexplore.ieee.org/document/9312000)

---

### 2.5 Intégration de code malveillant involontaire
Même sans intention malveillante, l’IA peut générer du code intégrant des dépendances contenant des malwares, des commandes exécutables ou des configurations vulnérables.  
Ces risques augmentent lorsque les prompts contiennent des instructions ambiguës ou complexes.  
La validation humaine est indispensable pour éviter qu’un code apparemment correct ne compromette l’intégrité du système.  
Les développeurs doivent examiner attentivement toutes les dépendances et configurations introduites par l’IA.  
La sécurité du projet repose donc sur la combinaison IA + supervision humaine.

**Sources :**  
- [ACM – Risks of AI-generated Dependencies](https://dl.acm.org/doi/10.1145/3460172)

---

## 3. Risques humains

### 3.1 Dépendance excessive
L’usage massif de l’IA peut réduire les [**compétences de base**](https://www.google.com/search?q=comp%C3%A9tences+de+base) des développeurs.  
Les équipes risquent de ne plus savoir coder sans assistance ou de mal comprendre le fonctionnement interne du code.  
Cette dépendance augmente la probabilité d’erreurs critiques lors de situations non couvertes par l’IA.  
Elle complique également la formation des débutants et la transmission de connaissances au sein des équipes.  
Une utilisation équilibrée de l’IA, combinée à un apprentissage actif, est essentielle pour limiter ces risques.

**Sources :**  
- [ACM Digital Library – Human Factors in AI](https://dl.acm.org/doi/10.1145/3313831)  
- [Stack Overflow Developer Survey 2023](https://survey.stackoverflow.co/2023/)

---

### 3.2 Illusion de compétence
Le développeur peut croire comprendre le code généré, même si l’essentiel provient de l’IA.  
Cette [**illusion de compétence**](https://www.sciencedirect.com/science/article/pii/S0742051X21001436) peut entraîner des décisions risquées et des erreurs critiques.  
Une confiance excessive dans le code IA sans validation peut provoquer des bugs et des failles de sécurité.  
Il est impératif de conserver une vigilance constante et d’effectuer des revues approfondies.  
Sans cette supervision, le code généré devient un facteur de risque plutôt qu’un outil d’accélération.

**Sources :**  
- [Dunning-Kruger Effect in Programming](https://www.sciencedirect.com/science/article/pii/S0742051X21001436)

---

### 3.3 Manque de revues de code sérieuses
Si les équipes considèrent que “l’IA a raison”, elles peuvent passer à côté de problèmes critiques.  
Le code peut contenir des incohérences, des vulnérabilités ou des mauvaises pratiques non détectées.  
Cette absence de relecture approfondie augmente la [**dette technique**](https://www.google.com/search?q=dette+technique) et complique la maintenance.  
Même un code fonctionnel peut devenir dangereux en production si des revues humaines rigoureuses ne sont pas effectuées.  
La supervision reste le pilier pour sécuriser l’usage de l’IA dans le développement.

**Sources :**  
- [Martin Fowler – Technical Debt](https://martinfowler.com/bliki/TechnicalDebt.html)

---

## 4. Risques organisationnels

### 4.1 Perte de cohérence dans l’architecture
Différents modules générés par l’IA peuvent violer les [**conventions de code**](https://www.google.com/search?q=conventions+de+code) et les [**patterns**](https://www.google.com/search?q=patterns) établis.  
La [**structure globale**](https://www.google.com/search?q=structure+globale) du projet peut perdre sa logique, rendant l’intégration difficile.  
Cette incohérence peut entraîner des bugs et des comportements inattendus.  
Le rôle des équipes humaines reste essentiel pour garantir l’uniformité et la cohérence du code.  
Sans supervision, le projet risque de devenir fragile et difficilement maintenable.

**Sources :**  
- [IEEE Software – Software Architecture](https://ieeexplore.ieee.org/document/9032331)

---

### 4.2 Dégradation du workflow de développement
L’IA peut générer du code sans respecter les [**guidelines internes**](https://www.google.com/search?q=guidelines+internes), contourner les processus standards et ignorer les pipelines CI/CD.  
Cela introduit des risques de bugs et de conflits non détectés automatiquement.  
Le workflow de l’équipe peut être perturbé, ce qui ralentit les livraisons et accroît la probabilité d’erreurs critiques.  
Un contrôle humain systématique est nécessaire pour sécuriser l’intégration et la livraison du code.  
L’IA doit être un assistant, pas un substitut aux processus établis.

**Sources :**  
- [Agile Alliance – Dev Workflow](https://www.agilealliance.org/glossary/devops/)

---

### 4.3 Faible reproductibilité
Le même prompt peut produire des versions différentes du code, parfois incompatibles.  
Cette variation peut provoquer des erreurs imprévues lors de tests ou en production.  
Les solutions générées peuvent être non vérifiables ou incohérentes avec le reste du projet.  
La supervision humaine et des tests systématiques sont essentiels pour limiter ces risques.  
La reproductibilité du code reste un enjeu majeur dans les projets utilisant l’IA.

**Sources :**  
- [ACM Transactions on Software Engineering – Reproducibility](https://dl.acm.org/doi/10.1145/3411764)

---

## 5. Risques juridiques

### 5.1 Propriété intellectuelle
Le code IA peut reproduire du code existant soumis à des licences restrictives.  
Il peut inclure des extraits protégés et enfreindre des obligations légales ou contractuelles.  
Ces risques légaux peuvent entraîner des sanctions ou des litiges coûteux.  
Un contrôle manuel des licences et une vérification des extraits sont donc indispensables.  
Le risque juridique est directement lié à la génération automatique de code.

**Sources :**  
- [GitHub Copilot Licensing FAQ](https://docs.github.com/en/copilot/getting-started-with-github-copilot/about-github-copilot#licensing)

---

### 5.2 Incompatibilité de licences
L’IA peut proposer des dépendances sous GPL, AGPL, LGPL ou d’autres licences contraignantes.  
Certaines licences imposent des obligations incompatibles avec des projets commerciaux.  
Ignorer ces contraintes peut provoquer des problèmes légaux et contractuels graves.  
Une revue humaine et juridique est indispensable pour éviter tout litige.  
Les risques juridiques sont donc amplifiés par l’usage non contrôlé de l’IA.

**Sources :**  
- [Open Source Initiative – License Types](https://opensource.org/licenses)

---

### 5.3 Confidentialité et protection des données
Selon l’outil utilisé, le code peut être envoyé sur des serveurs externes.  
Il peut contenir des [**données sensibles**](https://www.google.com/search?q=donn%C3%A9es+sensibles) ou des [**secrets**](https://www.google.com/search?q=secrets) accidentellement exposés.  
Ces fuites peuvent avoir des conséquences légales et sécuritaires graves.  
La gestion des informations confidentielles reste un enjeu critique pour l’utilisation de l’IA.  
Une politique stricte de sécurité et de contrôle des données est essentielle.

**Sources :**  
- [GDPR Compliance Guide](https://gdpr.eu/)  
- [OpenAI Data Usage Policy](https://openai.com/policies/data-usage)

---

## 6. Risques stratégiques

### 6.1 Perte de maîtrise du produit
Si trop de code est généré automatiquement par l’IA, le cœur du produit peut devenir difficile à expliquer et à maintenir.  
Les équipes risquent de perdre la compréhension technique du code et de dépendre entièrement de l’outil pour toute modification.  
Cette dépendance augmente les risques d’erreurs critiques, d’incohérences dans l’architecture et de retard dans la correction de bugs.  
La supervision humaine est indispensable pour garantir la cohérence et la qualité du produit final.  
Sans cette vigilance, l’IA peut devenir un facteur de fragilité plutôt qu’un accélérateur de productivité.

**Sources :**  
- [IEEE – Strategic Risks of AI](https://ieeexplore.ieee.org/document/9321122)

---

### 6.2 Risque de dépendance à un fournisseur
L’usage d’un modèle IA externe peut entraîner un [**vendor lock-in**](https://www.google.com/search?q=vendor+lock-in), avec des limitations imprévisibles.  
Des coûts supplémentaires, des changements de politique ou des interruptions de service peuvent affecter le projet.  
Cette dépendance peut compliquer la maintenance et l’évolution du code généré.  
La prudence impose de prévoir des alternatives et de ne pas centraliser toute la logique critique sur l’IA.  
Les risques stratégiques liés à la dépendance augmentent avec la complexité du projet et le volume de code généré.

**Sources :**  
- [Vendor Lock-in Risks – ACM](https://dl.acm.org/doi/10.1145/3460172)

---

## 7. Risques pédagogiques (chez les débutants)

### 7.1 Apprentissage superficiel
L’utilisateur peut développer des compétences limitées en codage s’il s’appuie trop sur l’IA.  
Il risque de ne pas comprendre les structures de données fondamentales ou la logique derrière le code généré.  
Cette dépendance entraîne des erreurs difficiles à corriger et des incompréhensions en cas de débogage nécessaire.  
La formation pratique reste indispensable pour éviter la perte de compétences de base.  
L’IA doit être utilisée comme un outil de renforcement, et non comme une substitution à l’apprentissage actif.

**Sources :**  
- [IEEE Transactions on Education](https://ieeexplore.ieee.org/document/9381001)

---

### 7.2 Mauvaise compréhension des erreurs
Les débutants peuvent ne pas savoir pourquoi le code généré échoue.  
Ils peuvent se concentrer sur les prompts plutôt que sur la logique, reproduisant des erreurs de manière répétée.  
Cette dépendance à l’IA augmente la probabilité de bugs critiques et d’erreurs en production.  
Un encadrement humain et des explications détaillées sont essentiels pour corriger ces dérives.  
Les risques pédagogiques sont donc directement liés à l’usage incontrôlé de l’IA.

**Sources :**  
- [ACM Education Reports](https://dl.acm.org/doi/10.1145/3429789)

---

### 7.3 Mauvaises habitudes codifiées
Exemples : copier-coller sans réflexion, absence de tests, dépendance aux prompts.  
Ces pratiques peuvent générer du code fragile, incohérent ou vulnérable.  
L’utilisateur perd l’habitude de raisonner sur le code, ce qui augmente les risques de bugs et de failles.  
L’IA peut amplifier ces comportements si elle est utilisée sans contrôle ou formation.  
Une pédagogie équilibrée reste indispensable pour former des développeurs compétents.

**Sources :**  
- [IEEE Software – Coding Practices](https://ieeexplore.ieee.org/document/9322211)

---

## 8. Risques liés à la gestion des prompts

### 8.1 Prompts mal formulés
Un prompt ambigu peut générer du code dangereux ou incohérent avec l’architecture du projet.  
Il peut provoquer des vulnérabilités, des duplications de code ou des erreurs logiques difficiles à détecter.  
La formulation correcte des prompts est donc essentielle pour limiter les risques.  
La relecture humaine et les tests automatisés restent des outils indispensables pour sécuriser le code généré.  
Les prompts mal conçus peuvent multiplier les erreurs et complexifier la maintenance.

**Sources :**  
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompting)

---

### 8.2 Fuite de contexte
Donner trop d’informations à l’IA peut provoquer des fuites accidentelles ou la divulgation de secrets.  
Une surcharge contextuelle peut entraîner des réponses imprécises ou du code incorrect.  
La supervision humaine est essentielle pour protéger les données sensibles et garantir la pertinence des suggestions.  
Les risques liés à la fuite de contexte sont particulièrement critiques pour les projets sécurisés ou confidentiels.  
L’IA ne comprend pas intrinsèquement la confidentialité des informations.

**Sources :**  
- [AI Privacy Risks – IEEE](https://ieeexplore.ieee.org/document/9387763)

---

### 8.3 Hallucinations techniques
L’IA peut inventer des fonctions ou des modules inexistants.  
Ces [**hallucinations techniques**](https://platform.openai.com/docs/guides/gpt-best-practices) peuvent introduire des erreurs graves en production.  
Les solutions théoriques proposées peuvent être techniquement irréalisables, rendant le code dangereux si utilisé sans vérification.  
La supervision humaine et les tests rigoureux sont essentiels pour détecter et corriger ces hallucinations.  
L’IA reste un générateur statistique et ne peut pas garantir l’exactitude technique.

**Sources :**  
- [OpenAI – AI Hallucinations](https://platform.openai.com/docs/guides/gpt-best-practices)

---

## 9. Fonctionnement de l’IA et système de tokens

L’IA générative fonctionne en analysant des séquences de [**tokens**](https://fr.vittascience.com/ia/text?localId=loc644547c3726ac0), qui représentent des unités de texte comme des mots ou parties de mots.  
Chaque prompt envoyé à l’IA est transformé en tokens, analysé par le modèle, puis la réponse est générée token par token.  
Cette approche permet à l’IA de prédire le mot suivant le plus probable en fonction du contexte.  
Cependant, cette prédiction statistique peut produire du code incorrect, incomplet ou vulnérable si le prompt est mal formulé ou si le modèle n’a pas accès au contexte complet.  
Comprendre le fonctionnement des tokens aide à anticiper les erreurs et à limiter les risques liés à la génération automatique de code.

**Sources :**  
- [VittaScience – Comprendre les tokens](https://fr.vittascience.com/ia/text?localId=loc644547c3726ac0)  
- [OpenAI – How GPT Works](https://platform.openai.com/docs/guides/gpt-best-practices)

---

# Conclusion

L’utilisation d’une IA pour coder est un outil puissant mais comporte de nombreux risques.  
Les principaux dangers concernent la sécurité, la cohérence du code, la dette technique, la dépendance humaine et juridique, ainsi que la compréhension réelle des programmes générés.  
Pour limiter ces risques, il est impératif de :  

- maintenir un contrôle humain systématique,  
- effectuer des tests rigoureux et continus,  
- auditer la sécurité et les dépendances,  
- vérifier la compatibilité et la cohérence architecturale,  
- encadrer les prompts et comprendre le système de tokens,  
- former les développeurs à utiliser l’IA comme un outil d’appoint, non un substitut.  

L’IA doit être un accélérateur de productivité et de créativité, et non un remplaçant du jugement et de la responsabilité humaine.

**Sources générales :**  
- [OpenAI Safety Best Practices](https://platform.openai.com/docs/guides/safety)  
- [ACM Digital Library – AI Risks](https://dl.acm.org/)  
- [IEEE Software – AI in Software Development](https://ieeexplore.ieee.org/)
