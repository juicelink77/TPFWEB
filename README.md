# Export web (neogeo-web-template)

Fichiers prêts pour jouer à **The Perfect Fighter** dans le navigateur via
[neogeo-web-template](https://github.com/Aurelien34/neogeo-web-template) (MAME WASM + GitHub Pages).

## Régénérer ces fichiers
Les CRC/SHA changent à CHAQUE build → relancer après un build :
```
python tools/make_web_export.py
```
Produit : `web/hash/NeoGeo.xml`, `web/roms/tpf.zip` (épuré aux 6 ROMs), `web/config.js`.

## Déploiement (une fois)
1. Sur GitHub, **Use this template** sur `Aurelien34/neogeo-web-template` → nouveau dépôt.
2. Uploader (interface web GitHub) :
   - `web/roms/tpf.zip`        → dossier **`roms/`**
   - `web/hash/NeoGeo.xml`     → dossier **`hash/`**
   - une jaquette **`cover.png`** → dossier **`images/`**
3. Remplacer `config.js` par `web/config.js` (et remplir `gameUrl`).
4. **Settings → Pages** → branche `main` → Save. L'URL apparaît en haut de la page Pages.

## À vérifier / pièges
- **BIOS Neo Geo** : MAME a besoin du BIOS `neogeo`. Le build WASM du template doit l'embarquer
  (ou fournir `neogeo.zip`). Si le jeu ne démarre pas, c'est le premier point à contrôler.
- **Poids** : `tpf.zip` ≈ 14,7 Mo compressé (VROM 16 Mo) → temps de chargement au 1er lancement.
- **Sprites brouillés ?** Les C-ROMs sont chargées entrelacées (`c1` offset 0, `c2` offset 1,
  `load16_byte`). Si les sprites sortent corrompus, inverser les deux `offset` (0 ↔ 1) dans
  `tools/make_web_export.py` (REGIONS → sprites) puis régénérer.
- **Nom MAME** = `tpf` (dans `NeoGeo.xml` `<software name>`, le zip `tpf.zip`, et `config.js` romName).
  Pour changer : `python tools/make_web_export.py <nom> "<description>" <année> <éditeur>`.
- La `softwarelist name="neogeo"` : c'est ce qu'attend le driver neogeo de MAME. Si le template
  utilise un autre nom de liste, adapter la ligne dans le script.

## Contenu attendu du zip (validé par MAME via NeoGeo.xml)
| ROM | Région MAME | Taille |
|-----|-------------|--------|
| tpf-p1.p1 | maincpu  | 1 Mo |
| tpf-s1.s1 | fixed    | 128 Ko |
| tpf-m1.m1 | audiocpu | 128 Ko |
| tpf-v1.v1 | ymsnd    | 16 Mo |
| tpf-c1.c1 | sprites (pair)  | 4 Mo |
| tpf-c2.c2 | sprites (impair)| 4 Mo |
