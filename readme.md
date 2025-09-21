# SDR++ (fork) — RFNM Source fixed for new `librfnm` API

This fork of [AlexandreRouma/SDRPlusPlus](https://github.com/AlexandreRouma/SDRPlusPlus.git) updates and fixes the **RFNM Source** module to work with the **latest `librfnm` API**.  
It keeps Soapy support and adds a clean, working RFNM native source for Ubuntu 24.04.

- Upstream repo: https://github.com/AlexandreRouma/SDRPlusPlus.git  
- This fork: https://github.com/chiaraberti13/SDRPlusPlus  
- Branch with the fix: `fix/rfnm-source-new-api`

## Why this fork?

Recent versions of `librfnm` changed the C++ API (class names, enums, and stream functions).  
The original `rfnm_source` in upstream SDR++ referenced legacy symbols (e.g., `librfnm`, `librfnm_transport::USB`, direct access to `dev->s`, etc.), causing compile errors or runtime symbol mismatches.  
This fork:
- Migrates to the **new `rfnm::device` API** from `librfnm`.
- Uses the correct enums (e.g., `rfnm::transport::TRANSPORT_USB`).
- Rewires RX stream setup and channel configuration through the new public setters.
- Builds and loads as a standard SDR++ plugin (`rfnm_source.so`).

> If you only want a one-shot automated installation of everything (librfnm, Soapy driver, SDR++ with RFNM), see:  
> https://github.com/chiaraberti13/rfnm-sdrpp-setup

---

## Supported platform

- **Ubuntu 24.04 LTS** (x86_64)

---

## Prerequisites

```bash
sudo apt update
sudo DEBIAN_FRONTEND=noninteractive apt install -y \
  build-essential cmake git pkg-config \
  libusb-1.0-0-dev libspdlog-dev libfftw3-dev libvolk-dev \
  libglfw3-dev libglew-dev libzstd-dev librtaudio-dev \
  libairspy-dev libairspyhf-dev librtlsdr-dev \
  libiio-dev libad9361-dev \
  libsoapysdr-dev soapysdr-tools
