# Transférer MG014.COM sur votre RC2014 avec Tera Term

Deux méthodes selon votre machine. Dans les deux cas : branchez votre
câble USB-série, ouvrez Tera Term sur le bon port COM à **115200 bauds**
(ou la vitesse de votre console), et assurez-vous d'être à l'invite CP/M.

---

## Méthode A — XMODEM (machines RomWBW : la plus rapide)

Votre machine a l'outil `XM` (RomWBW l'inclut). Alors :

1. Sur la machine, tapez :

```
XM R MG014.COM
```

   Elle affiche qu'elle attend une réception XMODEM.

2. Dans Tera Term : **File → Transfer → XMODEM → Send...** et choisissez
   le fichier `MG014.COM` (le binaire).

3. La barre de progression défile quelques secondes. À la fin, la machine
   revient à l'invite : c'est fait.

4. Vérifiez : `DIR MG014.COM` — puis lancez `MG014`.

---

## Méthode B — DOWNLOAD (style Grant Searle : universelle)

Si votre machine a `DOWNLOAD.COM` (les SBC de Grant Searle, la plupart
des configurations RC2014 classiques), on envoie `MG014.TXT` — un simple
fichier TEXTE qui contient le programme encodé. Aucun protocole : juste
du texte, mais avec des DÉLAIS pour laisser respirer le Z80.

1. **Réglez les délais dans Tera Term** (l'étape qu'on oublie toujours) :
   **Setup → Serial port...** →
   - *Transmit delay* : **3 msec/char** et **100 msec/line**
   - OK.

2. Sur la machine, assurez-vous d'être à l'invite (tapez Entrée).

3. Dans Tera Term : **File → Send file...** et choisissez `MG014.TXT`
   (cochez rien de spécial — c'est du texte).

4. Vous verrez la commande `A:DOWNLOAD MG014.COM` s'écrire toute seule,
   puis un long silence pendant que l'hexadécimal coule (~1 minute
   avec les délais ci-dessus). **Ne touchez à rien.**

5. À la fin, la machine affiche `OK` : le fichier est écrit et vérifié
   (somme de contrôle comprise). Si elle affiche `Checksum Error` ou
   reste muette : tapez `>0000` puis Entrée pour la dégager, augmentez
   les délais (5 msec/char), et recommencez.

6. Vérifiez : `DIR MG014.COM` — puis lancez `MG014`.

7. (Après coup, remettez les *Transmit delay* à 0 pour retrouver un
   clavier vif.)

---

## Premier lancement

- **Sans la carte MG014 installée** : le programme vous montre les
  adresses de votre machine et vous dessine la config des interrupteurs
  à régler AVANT d'insérer la carte.
- **Avec la carte** : il la trouve, l'éprouve à fond, exerce sa DEL, et
  écrit le certificat `MG014CRT.TXT`.

Bonne soudure!

— Richard Murray + Claude, l'atelier Zorton
