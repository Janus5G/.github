<div align="center">

<img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/banner.svg" alt="Janus — optical datapath, spectral storage, open toolchains" width="100%">

<br>

[![Sponsor](https://img.shields.io/badge/Sponsor-Janus5G-7C5CFF?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/Janus5G)
[![Profile](https://img.shields.io/badge/GitHub-Janus5G-0B1220?style=for-the-badge&logo=github&logoColor=22D3EE)](https://github.com/Janus5G)
[![Site](https://img.shields.io/badge/aagii.net-0B1220?style=for-the-badge&logo=googlechrome&logoColor=F5C14A)](https://www.aagii.net)
[![Location](https://img.shields.io/badge/Denmark-0B1220?style=for-the-badge&logo=openstreetmap&logoColor=34D399)](https://github.com/Janus5G)

**Independent systems architect and developer.**  
Programming languages · education and AI · Linux tools · distributed intelligence · experimental optical hardware.

</div>

---

## How it began

This work did not begin with a grand roadmap. Curiosity about why glass-crystal data storage had seen so little visible progress inspired early ChromaPlex experiments: a programming language, an assembly layer, a compiler and the Cplex editor. Questions about heat led to ChromaPlex OS v2. Later, the curved lid of a container inspired the next line of optical thinking that became PRISME. An idea sparked by a video about AI-to-AI communication led to ChromaSpeechAI and eventually ChromaNeural.

Other projects emerged from quite different problems. **ChromaLearn** addresses pupils using AI to bypass learning; **ChromaPress** grew from the need for dependable, user-friendly Linux ISO tools; **Project Pusher2** helps newcomers publish with GitHub. These projects deserve their own place, not a forced connection to optical computing.

**Security · Functionality · Usability** are guiding principles. Less unnecessary computation, less data traffic and better energy efficiency are objectives to measure—not performance claims that have already been established.

### Explore by interest

| Area | Start here |
| --- | --- |
| Learning with AI | [ChromaLearn](https://github.com/Janus5G/ChromaLearn) |
| Linux customization and development | [ChromaPress](https://github.com/Janus5G/ChromaPress) · [Coding Agent](https://github.com/Janus5G/Chromaplex-Coding-Agent) |
| Beginner-friendly GitHub tools | [Project Pusher2](https://github.com/Janus5G/project-pusher2) |
| Programming languages and optical research | [ChromaPlex OS](https://github.com/Janus5G/chromaplex-os) · [PRISME](https://github.com/Janus5G/PRISME) |
| Distributed AI collaboration | [ChromaNeural](https://github.com/Janus5G/ChromaNeural) |
| Hardware research | [Q8 Modular Base RevC](https://github.com/Janus5G/Q8_Modular_Base_RevC_RC1.2_GitHub_Desktop) |

---

## Architecture at a glance

```text
PROGRAMMING AND SOFTWARE EXECUTION
   Cplex (Rust/Slint editor)
       ├─ Danish CPL → textual CPA → CPA assembler → CrystalSimulator
       └─ simple CPL → separate legacy bytecode assembler → VM
   Brainfuck source → CPA translator → CPA assembler → CrystalSimulator

ARCHITECTURAL CONNECTIONS
   ChromaPlex OS
      └─ ChromaPlex OS v2 (57 facets, moving light, multi-crystal model)
          └─ PRISME (R/G/B/V quaternary payload + UV check symbol)
              ├─ PRISME Binary Extension (standalone binary packaging)
              ├─ Q8 hardware engineering and optical research directions
              └─ ChromaSpeechAI concepts → ChromaNeural development
                                         └─ Cubic-4-inspired task division
```

**Important distinction:** these are connected *ideas and software developments*, not one verified end-to-end hardware stack. The CPA/CrystalSimulator path and the legacy bytecode/VM path are distinct. CPA is a working software assembly language, **not yet a complete FPGA instruction processor** on Q8 hardware. Physical storage, optical links and performance-per-watt require laboratory validation.


---

<h2><img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/section-chromaplex.svg" alt="ChromaPlex — the foundation" width="100%"></h2>

[**ChromaPlex OS**](https://github.com/Janus5G/chromaplex-os) is an experimental language and simulation stack for colour-channel, voxel-addressed data structures and lossless exponent–remainder number representation.

| Layer | Verified role |
| --- | --- |
| **CPL — ChromaPlex Language** | Higher-level source language for values, coordinates, colour channels, voxel storage, and output. |
| **CPA — ChromaPlex Assembly** | Lower-level instruction language for registers, channel reads/writes, arithmetic, control flow, packing, and I/O. |
| **Assembler + simulator** | Validates CPA, then executes it against sparse software-modelled 3D crystal voxels. |
| **Representation** | Five logical channels: red, green, blue, violet, and UV; numeric values can use exponent–remainder pairs. |

The implemented primary flow is:

```text
CPL source → textual CPA → CPA assembler → CrystalSimulator
```

A separate **Brainfuck → CPA** translator is implemented in the ChromaPlex core. This is the verified compatibility input beyond CPL. No general translation layer for mainstream existing languages is claimed here.

### Toolchain and authoring

[**chromaplex-os-compiler**](https://github.com/Janus5G/chromaplex-os-compiler) contains a separate CPL/CPA/VM toolchain with a limited CPL parser, bytecode assembler, virtual machine, simulated storage, and laser-control abstraction.

[**Cplex**](https://github.com/Janus5G/Cplex) is the native Rust + Slint desktop editor for ChromaPlex/CPL. It uses a JSON bridge to bundled Python tooling and currently supports two CPL paths:

- **simple CPL** → legacy assembly/bytecode path;
- **Danish CPL** → CPA assembly plus a `CHROMAPLEX_CPA_BUNDLE_V1` editor/simulator bundle.

Cplex is development tooling around ChromaPlex; it is not the language foundation itself.

### ChromaPlex OS v2 — the next step

[**ChromaPlex OS v2**](https://github.com/Janus5G/chromaplex-os-v2) explores a **57-facet crystal model**, multiple crystals, **moving the light source instead of the crystal**, software-modeled lens capture and write-once registration. The existing [interactive software demonstration](https://janus5g.github.io/chromaplex-os-v2/demo/index.html) illustrates the concept; it does not establish physically tested glass storage. ChromaPlex OS v2 itself is unchanged by this profile update.

---

<h2><img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/section-prisme.svg" alt="From ChromaPlex to PRISME" width="100%"></h2>

[**PRISME**](https://github.com/Janus5G/PRISME) carries the colour-channel direction into a five-channel spectral byte mapping.

```text
one byte
  │
  ├── R, G, B, V: four base-4 symbols = 8 payload bits
  └── UV: (R + G + B + V) mod 4 verification value
```

The four visible data channels represent all 256 byte values. UV is a **verification channel**, not a complete arbitrary multi-error ECC by itself. Higher-level error correction remains a separate layer.

### Software evidence

| Evidence | What is supported | Classification |
| --- | --- | --- |
| All 256 byte values | Encode → UV-check → decode in [PRISME's published Python tests](https://github.com/Janus5G/PRISME/blob/main/tests/test_prisme.py) | Reproducible software logic |
| Single-channel corruption | 3,840 / 3,840 nonzero one-channel level changes detected by the modulo-4 check | Exhaustive mathematical/software check |
| Reed–Solomon correction | Public tests document the arithmetic of error/erasure limits | **Reference calculation**, not integrated optical correction evidence |
| Physical optical operation | Channel separation, noise, BER, write/read speed, power and durability | **Physical verification pending** |

The four R/G/B/V channels carry **8 payload bits** (one byte) per modeled optical symbol; UV provides a separate **2-bit integrity value**. Those are **not 10 independent payload bits**. UV detects single-channel level alterations but does not itself correct errors and may miss compensating multi-channel changes. Older precise long-run benchmark counts have been omitted from the profile because independent reproduction evidence for those runs is not available in the current public PRISME source tree.

A passive glass medium might retain information without standby electricity. **That does not mean an operating reader, writer, server or datacenter uses zero power.** Efficiency claims require measured, comparable baselines.


---

<h2><img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/section-directions.svg" alt="One foundation — multiple directions" width="100%"></h2>

### Conventional-system interoperability

[**PRISME Binary Extension**](https://github.com/Janus5G/PRISME-Binary-Extension) is a **separate experimental repository** for portable packaging for conventional binary systems.

It converts structured data or binary payloads into portable `.prisme` packages and can emit raw binary, manifests, and C/Rust-compatible byte arrays. The package format defines payload type, optional zlib compression, lengths, CRC-32, SHA-256, package ID, timestamp, and JSON manifest metadata.

> Status: **experimental specification and reference implementation; not production-validated**. Its own rights-reserved license governs use, separate from the terms of other projects.

This extension is separate from PRISME's spectral mapping and is not a mandatory runtime dependency for ChromaPlex or PRISME.

### Node and AI communication

**ChromaSpeechAI** is the color-symbol communication approach developed for AI-to-AI exchange and used in the ChromaNeural direction. Its optical proposal has **four data colors, with seven shades each (28 base symbols)**; **UV is reserved for verification/control**, not a fifth data color. The representation was inspired by the PRISME work but is not identical to PRISME's four-level-per-channel byte mapping.

[**ChromaNeural**](https://github.com/Janus5G/ChromaNeural) is being developed to distribute tasks across AI nodes, combine and check results, and reuse useful verified knowledge. Its **current public README** identifies RC4 as withdrawn and RC5 as forthcoming. Internal development and reported tests are not the same as a complete published verification package.

| Research area | Status |
| --- | --- |
| ChromaSpeechAI network-based communication | Implementation and LAN/WAN tests reported by the developer; publicly reproducible release evidence pending |
| Cubic-4-inspired task division, knowledge sharing and reuse | Development underway; complete workflow verification pending |
| Optical lamp-and-camera communication | Physical distinction of shades, timing, UV/control readout, BER and throughput remain to be measured |
| Fewer repeat queries and lower data/energy costs | Hypotheses to benchmark, not established general savings |

### Dedicated physical direction

Three public, separate Q8 hardware projects provide engineering material and software models. **None is a fabricated, physically verified optical computing system.**

- [**Q8 Hybrid Optical Hardware v0.2.1**](https://github.com/Janus5G/Q8-Hybrid-Optical-Hardware-v0.2.1) — classical 256-vertex Q8 graph, MZI/FPGA research references and an [interactive mathematical demo](https://janus5g.github.io/Q8-Hybrid-Optical-Hardware-v0.2.1/interactive/index.html). **Fabrication HOLD**: nominal source dimensions **360 × 260 × 116 mm** versus STL bounding box **348 × 250 × 116 mm** ([documented CAD check](https://github.com/Janus5G/Q8-Hybrid-Optical-Hardware-v0.2.1/blob/main/docs/CAD_CHECKS.md)).
- [**Q8 Optical DIY Maker RevA**](https://github.com/Janus5G/Q8-Optical-DIY-Maker-RevA) — ESP32-S3-based optical/motion research reference with CAD files, firmware protected by disabled actuation defaults and a [GitHub Pages project site](https://janus5g.github.io/Q8-Optical-DIY-Maker-RevA/website/). Physical safety and dimensional fit need independent review.
- [**Q8 Modular Base RevC RC1.2**](https://github.com/Janus5G/Q8_Modular_Base_RevC_RC1.2_GitHub_Desktop) — a **300 × 180 mm, four-layer motherboard concept** with Lattice FPGA, ESP32-S3, four reserved expansion interfaces, reference SystemVerilog, engineering BOM, [website](https://janus5g.github.io/Q8_Modular_Base_RevC_RC1.2_GitHub_Desktop/website/) and [interactive software demo](https://janus5g.github.io/Q8_Modular_Base_RevC_RC1.2_GitHub_Desktop/demo/). Follow its [live software CI](https://github.com/Janus5G/Q8_Modular_Base_RevC_RC1.2_GitHub_Desktop/actions/workflows/revc-ci.yml); FPGA timing and physical measurements remain pending.

Datacenter optical-delay hardware, GPU/e-sport expansion, ArenaLink-8 and fiber-coil winding machines are distinct future directions; they are **not** finished or validated RevC plug-in modules. The Q8 projects carry **limited research/evaluation licenses**, not unrestricted OSI open-source hardware licenses.

### Independent projects — learning, Linux and accessible development

These projects were built to address different real-world problems. They belong alongside the optical work, rather than underneath it.

- [**ChromaLearn**](https://github.com/Janus5G/ChromaLearn) — AI as a **learning helper, not an answer shortcut**. The published **0.4.5 evaluation release** includes school roles and session-only student data handling within the app. **Version 2 is under development**; it must not be presented as already released.
- [**ChromaPress**](https://github.com/Janus5G/ChromaPress) — a Linux ISO customization, building and verification desktop workbench. The public **v1.0.0a72 alpha** includes evidence for a generated ISO booting in a VirtualBox live session; this is not proof of compatibility with every Linux installation or device.
- [**Project Pusher2**](https://github.com/Janus5G/project-pusher2) — an approachable GUI for GitHub staging, commits and pushing. The public README describes **v1.1.0** with opt-in automated releases for supported Electron projects.
- [**ChromaPlex Coding Agent**](https://github.com/Janus5G/Chromaplex-Coding-Agent) — a Linux coding/build environment (**v0.4.0 alpha**) with source integrity controls and target-aware security policy for desktop, web, embedded systems and CPL/CPA. Full GUI, target-device deployment and physical embedded validation remain outstanding.

A separate **custom Linux** and industrial device-programming direction is being developed to combine source-language tools, verification and deployment. Its proposed Raspberry Pi/ESP32/Arduino targets are not claimed to have been production-validated.


---

<h2><img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/section-status.svg" alt="Engineering status" width="100%"></h2>

| Capability | Evidence-based status |
| --- | --- |
| Documented CPL subset, CPA assembler and CrystalSimulator | Implemented in software |
| Brainfuck → CPA adapter | Implemented |
| Separate simple-CPL → bytecode → VM route | Implemented legacy software path |
| Cplex Rust/Slint editor and Python bridge | Implemented developer tooling |
| ChromaPlex OS v2 57-facet/multi-crystal architecture | Software model; physical storage unverified |
| PRISME one-byte R/G/B/V mapping and UV single-channel checks | Reproducible software model |
| PRISME Binary Extension | Separate experimental packaging format |
| Reed–Solomon / UV optical ECC | Reference calculations; physical operation unverified |
| Automatic CPL/CPA → FPGA → optical storage chain | **Not verified end-to-end** |
| ChromaSpeechAI optical lamp-to-camera link | **Physical verification pending** |
| ChromaNeural public release | RC4 withdrawn; RC5 forthcoming per public README |
| Cubic-4-inspired distributed work and knowledge reuse | In development |
| Q8 hardware source/reference models | Published with software test evidence |
| Q8 Hybrid dimensional fit | **HOLD: CAD/STL mismatch** |
| Q8 physical BER, timings and power savings | **Not physically verified** |
| ChromaLearn | Public 0.4.5 evaluation; v2 in development |
| ChromaPress | Public 1.0.0a72 alpha; documented VM live-ISO verification |
| Project Pusher2 | Documented v1.1.0 and release-workflow support |
| ChromaPlex Coding Agent | Public v0.4.0 alpha; real hardware testing pending |

---

<h2><img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/section-project-map.svg" alt="Project map" width="100%"></h2>

### ChromaPlex, compilers and spectral research

- [**ChromaPlex OS**](https://github.com/Janus5G/chromaplex-os) — CPL/CPA, assembler and 3D crystal simulator.
- [**ChromaPlex OS Compiler**](https://github.com/Janus5G/chromaplex-os-compiler) — parallel compiler, bytecode/VM and simulated storage tools.
- [**Cplex**](https://github.com/Janus5G/Cplex) — Rust/Slint CPL desktop editor.
- [**ChromaPlex OS v2**](https://github.com/Janus5G/chromaplex-os-v2) — 57-facet addressing and multi-crystal software models.
- [**PRISME**](https://github.com/Janus5G/PRISME) — spectral byte mapping and optical research.
- [**PRISME Binary Extension**](https://github.com/Janus5G/PRISME-Binary-Extension) — experimental binary packaging for existing systems.

### Optical and modular hardware research

- [**Q8 Hybrid Optical Hardware v0.2.1**](https://github.com/Janus5G/Q8-Hybrid-Optical-Hardware-v0.2.1) — Q8/MZI models; mechanical fabrication HOLD.
- [**Q8 Optical DIY Maker RevA**](https://github.com/Janus5G/Q8-Optical-DIY-Maker-RevA) — maker-oriented optical and motion hardware reference.
- [**Q8 Modular Base RevC RC1.2**](https://github.com/Janus5G/Q8_Modular_Base_RevC_RC1.2_GitHub_Desktop) — FPGA-controlled modular motherboard concept.

### Distributed AI, education and developer tools

- [**ChromaNeural**](https://github.com/Janus5G/ChromaNeural) — distributed AI collaboration and knowledge reuse.
- [**ChromaLearn**](https://github.com/Janus5G/ChromaLearn) — responsible school AI and student learning.
- [**ChromaPress**](https://github.com/Janus5G/ChromaPress) — Linux ISO creation and validation.
- [**Project Pusher2**](https://github.com/Janus5G/project-pusher2) — beginner-friendly GitHub publishing.
- [**ChromaPlex Coding Agent**](https://github.com/Janus5G/Chromaplex-Coding-Agent) — development and secure-build tooling.

All repositories retain their own **licensing terms and validation boundaries**. Software models and rendered concepts must not be presented as already-tested physical hardware.


---

<div align="center">

Sponsorship supports public compilers, simulators, specifications and engineering documentation.  
It does not sell equity, tokens or exclusive rights to public work.

**[github.com/sponsors/Janus5G](https://github.com/sponsors/Janus5G)**

</div>
