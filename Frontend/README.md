# Frontend — WellNest

Application web Angular de la plateforme WellNest (interface adaptée aux seniors).

> Dossier prêt à recevoir le projet Angular. Pour le générer ici :
>
> ```bash
> cd frontend
> ng new wellnest-ui --directory . --routing --style=scss
> ```

## Principes d'interface (voir la maquette UI/UX)

- Police Atkinson Hyperlegible, texte de 20 px minimum
- Contraste du texte d'au moins 7:1 (WCAG AAA)
- Boutons d'au moins 60 px de haut, toujours une icône + un mot
- Une action principale par écran, bouton « Retour » toujours visible

## Communication avec le backend

Toutes les requêtes passent par l'API Gateway (`http://localhost:8080/api/msX/...`),
avec le jeton JWT obtenu auprès de Keycloak.
