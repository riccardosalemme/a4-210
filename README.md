# a4-210

## Todo

- [ ] Modifica persistente driver wifi
- [ ] Kiosk mode su Sway
- [ ] Verifica funzionamento uscita audio
- [ ] Stampante termica
- [ ] Monitor esterno via HDMI

## Hardware

|   |   |
|---|---|
| CPU | Intel Atom x5-Z8350 @ 1.44 GHz (Cherry Trail) |
| GPU | Intel HD 400, driver `i915` |
| Storage | eMMC 16 GB (`mmcblk1`) |
| WiFi | Broadcom **BCM43430/1** su SDIO, modulo **AP6212** |
| DMI | `sys_vendor` e `product_name` = `Default string` |

## Configurazione minimale

BIOS Password `smart?ecp`

Pacchetti essenziali
```sh
apk update
apk add nano htop git firefox chromium font-dejavu font-noto-emoji font-noto
```

Installazione di Sway
```sh
setup-desktop sway
```

## Configurazione Wifi

> Il firmware di default di Alpine (linux-firmware-brcm) imposta una frequenza del quarzo errata (xtalfreq=37400 invece di 26000) per il modulo Wi-Fi AP6212 (BCM43430/1).

```sh
git clone https://github.com/riccardosalemme/a4-210.git
cd a4-210/firmware

# Sostituzione con firmware OS originale
cp -f brcmfmac43430-sdio.bin brcmfmac43430-sdio.txt /lib/firmware/brcm/

rm -f /lib/firmware/brcm/brcmfmac43430-sdio.*.zst /lib/firmware/brcm/brcmfmac43430-sdio.clm_blob*
```

