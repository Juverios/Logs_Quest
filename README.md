# Logs_Quest WCS

### Challenge :

    1.Installe un serveur web (Apache ou Nginx) sur une machine virtuelle Linux
    2.Configure le logging pour enregistrer les accès et les erreurs
    3.Génère du trafic sur le serveur web (utilise des outils comme curl ou un navigateur)
    4.Analyse les logs générés et identifie :
        - Les requêtes réussies (code 200)
        - Les erreurs 404 (page non trouvée)
        - Les adresses IP les plus fréquentes
-------------------
### Critères d'acceptations
Ton serveur web est correctement configuré et génère des logs.
Logs générés par le serveur Nginx : 

``::1 - - [08/Jun/2025:11:31:21 +0200] "GET / HTTP/1.1" 200 615 "-" "curl/8.5.0"`` => **Requêtes réussie**

``::1 - - [08/Jun/2025:11:31:40 +0200] "GET /doesnotexist.html HTTP/1.1" 404 162 "-" "curl/8.5.0"`` => **Erreur 404**

``::1 - - [08/Jun/2025:11:31:53 +0200] "GET /index.html HTTP/1.1" 404 162 "-" "curl/8.5.0"`` => **Erreur 404**

-------------------

Configuration des logs :

| Élément                        | Description                                                    |
| ------------------------------ | -------------------------------------------------------------- |
| `::1`                 | Adresse IP du client                                           |
| `-`                            | Nom de l'utilisateur distant              |
| `-`                            | Nom d’utilisateur authentifié                  |
| `[08/Jun/2025:14:34:56 +0000]` | Date et heure de la requête (format Apache/Nginx log)          |
| `"GET /index.html HTTP/1.1"`   | Méthode HTTP, URI demandé, et version du protocole             |
| `200`                          | Code de réponse HTTP (200 = OK, 404 = Not Found          |
| `612`                          | Taille de la réponse en octets (hors en-têtes)                 |
| `"-"`                          | Référent HTTP  |
| `"Mozilla/5.0"`                | User-Agent du client (navigateur)               |


