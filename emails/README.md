# Emails MétroChain

Templates des emails transactionnels envoyés par Supabase Auth.

## Installation

Les templates ne sont pas lus depuis ce dépôt : Supabase les stocke côté projet.
Il faut donc les coller dans le dashboard après chaque modification.

1. Ouvrir [Authentication → Emails → Templates](https://supabase.com/dashboard/project/ziipyiwsxefecwjwqjnw/auth/templates)
2. Onglet **Confirm signup**
3. Champ **Subject heading** :

   ```
   Confirme ton adresse pour activer ton compte MétroChain
   ```

4. Champ **Message body** : coller le contenu de [`confirmation-inscription.html`](confirmation-inscription.html)
5. **Save**

Tester ensuite avec une adresse jetable via le bouton « Créer un compte » du site.

## Variables Supabase utilisées

| Variable              | Contenu                                              |
| --------------------- | ---------------------------------------------------- |
| `{{ .ConfirmationURL }}` | Lien de confirmation (bouton + lien de secours)   |
| `{{ .Email }}`        | Adresse du destinataire, affichée en pied de page     |

Autres variables disponibles si besoin : `{{ .Token }}` (code à 6 chiffres),
`{{ .TokenHash }}`, `{{ .SiteURL }}`, `{{ .RedirectTo }}`.

## Contraintes d'écriture

Les clients mail ne sont pas des navigateurs. Le template respecte donc :

- mise en page en `<table>`, pas de flex ni de grid ;
- CSS **en ligne** uniquement, aucune balise `<style>` ni classe ;
- pas de SVG (Gmail le bloque) — le logo « M » est une cellule sombre avec la
  lettre en Arial Black, ce qui rend partout ;
- `border-radius` ignoré par Outlook desktop : les blocs y apparaissent carrés,
  c'est voulu et sans conséquence ;
- bandeau supérieur en rectangles de couleurs de lignes plutôt qu'en pastilles
  rondes, pour le même motif.

## Aperçu

Ouvrir le fichier HTML directement dans un navigateur donne un rendu fidèle,
les variables `{{ .Xxx }}` restant affichées telles quelles.
