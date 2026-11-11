# Goldshell SC5 Pro II Firmware Research

Independent community research into firmware for the **Goldshell SC5 Pro II** (also written **SC5 Pro Ⅱ**) ASIC miner, including firmware architecture, upgrade mechanisms, recovery research, hardware configuration, and reverse engineering.

## Stock Firmware Package 2.2.0

| Property | Value |
|---|---|
| Manufacturer | Goldshell (file labeled for Goldshell; manufacturer authenticity not independently verified) |
| Model | **SC5 Pro II / SC5 Pro Ⅱ** (per provided filename) |
| Version | 2.2.0 (filename and embedded image header) |
| Package | `firmware-Goldshell-SC5ProⅡ-2.2.0.cpb` |
| Format | `.cpb` firmware update package |
| Package size | 33,985,536 bytes |
| Control-board identifier | `MCB_V4_3` **in package header**; physical board compatibility not independently confirmed |
| Intended use | Preservation and community firmware research; application to hardware untested |

**[Firmware releases](https://github.com/booozytheclown/goldshell-sc5proii-firmware/releases)** — download the `.cpb` package and checksum from the `stock-2.2.0` release **once published**.

### Important format and model warnings

**This is a `.cpb` update package, NOT a standalone raw microSD recovery image (`burn-*.img`).** Do not write the `.cpb` directly to a microSD card or treat it as the bootable recovery image from the HS Box project. A true SD recovery image must be obtained separately from Goldshell if needed.

The file is labeled for the **SC5 Pro II**, not the original SC5 Pro / SC5 Pro I, SC Lite, SC Box, or other Goldshell models. Do not cross-flash between models or hardware revisions. Confirm compatibility with Goldshell and your device's control-board information before attempting an update.

### SHA-256 integrity verification

Package:

`firmware-Goldshell-SC5ProⅡ-2.2.0.cpb`

Calculated SHA-256:

`8f4ef40632a9ab276ea3f5cfefc5ad1f076cd33a254b8f7fd61d7e493ed15a83`

Linux/macOS (place `.cpb` and `.sha256` together):

```bash
sha256sum -c 'firmware-Goldshell-SC5ProⅡ-2.2.0.cpb.sha256'
```

Windows PowerShell:

```powershell
Get-FileHash -LiteralPath '.\firmware-Goldshell-SC5ProⅡ-2.2.0.cpb' -Algorithm SHA256
```

Compare the PowerShell result against the SHA-256 above. The checksum was calculated from the original supplied file without modification. It demonstrates file integrity relative to this publication, **not** independent manufacturer authentication or a safety audit.

### Read-only package observations

- Outer `.cpb` header identifies an embedded `firmware-MCB_V4_3.tgz` package.
- The archive begins after a 512-byte outer header and contains `firmware.ius` and `firmware.ius.sig`.
- The `firmware.ius` header contains version `2.2.0`.
- The signature file exists, but its cryptographic validity and signing trust chain have **not** been verified.
- The package has **not** been installed or tested on an SC5 Pro II here.

These observations do not by themselves prove the target hardware revision or rule out hidden issues in the software.

## Official references

- [Goldshell's firmware repository](https://github.com/goldshellminer/firmware) (availability of this exact SC5 Pro II package there was not confirmed at publication preparation time)
- [Goldshell: Upgrade Miner Firmware](https://goldshellhelp.zendesk.com/hc/en-us/articles/16805936980633-Upgrade-Miner-Firmware)
- [Goldshell support](https://goldshellhelp.zendesk.com/hc/en-us/requests/new)

## Research objectives

- Preserve manufacturer-provided firmware packages with reproducible hashes.
- Document `.cpb` container structure, embedded image formats, signature and validation behavior.
- Investigate firmware upgrading, recovery options, and device compatibility.
- Explore hardware monitoring, fan/thermal controls, and software architecture.
- Share reproducible independent analysis and encourage community contributions.

## Contributing

Issues, pull requests, documentation, and independent research are welcome. Please distinguish verified observations from hypotheses and untested experiments. Do not publish passwords, private keys, device credentials, wallet information, serial numbers, or other sensitive information.

## Disclaimer

This project is independent and is **not affiliated with or endorsed by Goldshell**. Original firmware and manufacturer documentation remain subject to their respective intellectual property rights; their inclusion does not claim to relicense proprietary components.

Updating or modifying firmware can cause data loss, device failure, or hardware damage. No guarantee is made regarding manufacturer authenticity, signature validity, compatibility, safety, or fitness for use. Only proceed on compatible hardware with a manufacturer-confirmed recovery path.
