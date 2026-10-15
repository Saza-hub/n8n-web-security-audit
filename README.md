# Audit sécurité web — n8n

Workflow n8n pour un **audit de configuration web non intrusif**, sur des sites clients dont l'audit est couvert par une **autorisation écrite**.

## Installation

1. Télécharger `workflows/audit_web_clients_autorises_premium_V3.json`.
2. Dans n8n : nouveau workflow → menu `⋯` → **Import from File**.
3. Modifier le nœud **Paramètres de l’audit** :
   - `url` : URL HTTPS complète à auditer.
   - `authorized_domain` : domaine autorisé (hôte).
   - `authorization_confirmed` : `true` uniquement après réception de l'autorisation écrite.
   - `authorization_reference` : référence interne de l'autorisation.
4. Vérifier le domaine, le périmètre autorisé, la fenêtre de test et les conditions contractuelles.
5. Exécuter manuellement, puis télécharger le rapport depuis le nœud de génération PDF (champ binaire `rapport_pdf`).

## Contrôles et livrable

- Contrôles HTTP `HEAD`, `GET` et `OPTIONS`.
- Vérifications indicatives des protections HTTPS, des en-têtes HTTP, des cookies et d'indices CORS.
- Classement des observations, explications vulgarisées, recommandations.
- Rapport PDF A4 présentant les constats **sans afficher les adresses IP**.

**Limites :** ce workflow n'est pas un test d'intrusion, ne simule pas d'exploitation de vulnérabilité et ne certifie pas l'absence de failles. Les données issues des réponses HTTP peuvent varier selon les pages et les serveurs. Vérifier la compatibilité avec la version n8n utilisée.

## Confidentialité et autorisation

Les IP sont masquées dans le rapport, mais les requêtes HTTP ne sont **pas anonymes** : l'hébergeur peut enregistrer l'IP de sortie n8n. Ne pas importer des secrets ou des autorisations contenant des données personnelles dans le dépôt. Le workflow ne contient pas d'identifiants de service.

Le dépôt est privé par défaut ; avant publication publique, vérifier les fichiers et supprimer les éventuelles données clients.
