# MG014.COM — companion test tool for the MG014 card

**v2.3 (2026-08-20) — Zorton, real-hardware assurance**
*Version française : [LISEZMOI.md](LISEZMOI.md)*

The companion program for the **MG014 parallel interface card**
(82C55, DB25 port) on RC2014 / CP/M 2.2+. It walks the card from
purchase to certification — you are in the right place.

```
                 __/\__
                 \    /      *  EPROUVE ZORTON  *
                 /_  _\      the star is only
                   \/        given on merit
```

## What it does

Run `MG014` — it detects the situation by itself:

**Card NOT installed yet → the ADVISOR**
- scans YOUR machine's port space (announcing each base before
  probing it), shows which bases are taken and which are free;
- recommends a base and **draws the DIP switch block on screen** —
  A2 at the top like on the card, each slider shown in its OFF or ON
  column. Put the card next to the screen, match the picture, done —
  *before* you ever insert it.

**Card installed → the CERTIFIER**
- finds the card wherever the switches put it;
- proves the internal mechanics: port A/B/C latches (patterns
  00 FF 55 AA plus a walking bit — 96 write-read cycles), register
  decoding, bit-by-bit BSR set/reset on port C;
- exercises the onboard LED (three blinks, then a walking-bit chase
  that names each pin on screen as it fires);
- returns the card to its safe state (all inputs, the reset state);
- writes the printable certificate: `MG014CRT.TXT`.

## Getting it onto your machine

1. Download **`MG014.COM`** (the binary) — or **`MG014.TXT`**
   (the same program as a plain-text DOWNLOAD package).
2. Follow **[GUIDE-TRANSFERT.md](GUIDE-TRANSFERT.md)** — Tera Term,
   two methods: XMODEM (RomWBW machines) or DOWNLOAD (Grant
   Searle-style classics). The guide is in French, but the menus and
   commands shown are the same in any language.
3. Type `MG014`. That's it.

## It speaks French

That's the native language of the workshop that built it — and a
verdict reads the same everywhere. The five words you'll meet:

| French | English |
|---|---|
| `0 faute` | zero faults |
| `EPREUVE` | test |
| `CONFORME` | pass |
| `libre` / `occupee` | free / taken |
| `SAINE` | healthy |

## In this folder

| File | What it is |
|---|---|
| `MG014.COM` | the program (CP/M binary, 4.4 KB) |
| `MG014.TXT` | the same program as a DOWNLOAD text package |
| `GUIDE-TRANSFERT.md` | how to transfer it with Tera Term |
| `LISEZMOI.md` | the French README |
| `MG014CRT-EXEMPLE.TXT` | a real certificate from our bench |

## Safety

The probe only fires inside the **20–6F window**; system zones
(memory paging, console UARTs, CompactFlash) are protected — the
result of a real bench investigation. Run it on an idle machine.

## License

(c) 2026 Richard Murray + Claude — free for personal use, commercial
by arrangement.

*— Richard Murray + Claude, l'atelier Zorton*
