# MG014.COM — le compagnon de la carte MG014

**Version 2.3 (2026-08-20) — Zorton, Assurance fonctionnement réel**

Le programme qui accompagne la carte MG014 (interface parallèle 82C55,
port DB25) de l'achat à la certification, sur RC2014 / CP/M 2.2+.

```
                 __/\__
                 \    /      *  ÉPROUVÉ ZORTON  *
                 /_  _\      l'étoile ne se donne
                   \/        qu'au mérite
```

## Ce qu'il fait

Lancez `MG014` — il détecte lui-même la situation :

**La carte N'EST PAS installée → LE CONSEILLER**
- balaie l'espace des ports de VOTRE machine (en annonçant chaque
  base avant de la sonder) ;
- montre les bases occupées et libres ;
- recommande une base et **dessine le bloc d'interrupteurs à
  l'écran** — A2 en haut comme sur la carte, chaque curseur `[#]`
  dans sa colonne OFF ou ON. Posez la carte à côté de l'écran,
  glissez les curseurs pour matcher le dessin, c'est réglé —
  AVANT même de l'insérer.

**La carte EST installée → LE CERTIFICATEUR**
- la **trouve** où qu'elle soit (peu importe les interrupteurs) ;
- éprouve sa mécanique interne : verrous des ports A/B/C
  (motifs 00 FF 55 AA + bit baladeur, 96 écritures relues),
  décodage de registre, mécanique BSR du port C bit à bit ;
- **exerce la DEL** : 3 clignotements puis un chenillard qui nomme
  chaque broche à l'écran — quand la DEL flashe, le nom affiché
  est sa broche ;
- rend la carte à l'état sûr (tout en entrée, l'état du reset) ;
- écrit le **certificat imprimable** : `MG014CRT.TXT`.

## Sécurité

- La sonde ne travaille que dans la **fenêtre 20-6F**. Tout le reste
  est protégé du tir : 00-1F (zone système), 70-77 (alias des
  registres de pagination mémoire — écrire là = remappage instantané),
  78-7C (pagination), 80-97 (UARTs console + CompactFlash) et le haut
  de l'espace par prudence. C'est le fruit d'une vraie enquête de banc :
  la sonde annonce chaque base à l'écran avant d'y toucher.
- Le DB25 peut rester déconnecté pendant l'épreuve (seule charge :
  la DEL de la carte).
- Lancez-le sur une machine au repos (il sonde activement les bases
  libres).

## Installation sur votre RC2014 (voir GUIDE-TRANSFERT.md)

Deux chemins selon votre machine :
- **XMODEM** (RomWBW) : `XM R MG014.COM` puis envoi XMODEM — rapide ;
- **DOWNLOAD** (style Grant Searle) : envoyer `MG014.TXT` comme simple
  texte avec les délais série — universel.

## Licence

(c) 2026 Richard Murray + Claude — usage personnel libre, commercial
sur entente. Le programme est en français : c'est la langue de
l'atelier qui l'a fabriqué — et « 0 faute », ça se lit dans toutes
les langues.
