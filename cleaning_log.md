## Problèmes détectés dans le dataset

- **Type de véhicule mal écrit** : 6 noms différents pour seulement 3 types de véhicules (ex : `e-bike`, `E-BIKE` et `electric_bike` = la même chose ; `scooter` et `TROTTINETTE` = la même chose).
- **Date au mauvais format** : `start_time` est du texte, pas une vraie date, donc on ne peut pas faire de calculs dessus.
- **Stations d'arrivée manquantes** : 407 trajets n'ont pas de `end_station_id` (environ 6 % des données).
- **Batterie suspecte** : les vélos mécaniques n'ont pas de batterie, pourtant `battery_start_pct` est toujours rempli, donc il y a probablement des fausses valeurs.
- **Distance en double** : `distance_km` et `distance_meters` disent la même chose, il faut vérifier qu'elles sont cohérentes.
- **Prix à vérifier** : le prix devrait correspondre à durée × tarif par minute, il faut contrôler que c'est bien le cas.
- **À vérifier ensuite** : valeurs impossibles (durées ou distances négatives, prix négatifs) et trajets en double.
