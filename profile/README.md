<div align="center">

<img src="https://raw.githubusercontent.com/Janus5G/.github/main/profile/banner.svg" alt="Janus — optical datapath, spectral storage, open toolchains" width="100%">

<br>

[![Sponsor](https://img.shields.io/badge/Sponsor-Janus5G-7C5CFF?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/Janus5G)
[![Profile](https://img.shields.io/badge/GitHub-Janus5G-0B1220?style=for-the-badge&logo=github&logoColor=22D3EE)](https://github.com/Janus5G)
[![Site](https://img.shields.io/badge/aagii.net-0B1220?style=for-the-badge&logo=googlechrome&logoColor=F5C14A)](https://www.aagii.net)
[![Location](https://img.shields.io/badge/Denmark-0B1220?style=for-the-badge&logo=openstreetmap&logoColor=34D399)](https://github.com/Janus5G)

**Systems architect and hardware developer.**  
Open work on optical datapath, spectral storage and the compilers that sit on top of them.

</div>

---

## Architecture at a glance

```text
CPL source                               Brainfuck source
   │                                           │
   │ CPL compiler                              │ implemented adapter
   ▼                                           ▼
CPA — ChromaPlex Assembly  ◄───────────────────┘
   │
   ├── assembler → validated instructions → CrystalSimulator
   │                                      → software-modelled 3D voxels
   │                                        + R/G/B/V/UV channels
   │
   └── parallel legacy toolchain → bytecode → VM + simulated crystal storage
                                             │
                                             ▼
                                  ChromaPlex representation foundation
                                             │
                                             │ architectural lineage;
                                             │ PRISME carries color-channel direction
                                             ▼
                              PRISME spectral byte representation
                              R/G/B/V quaternary payload + UV VERIFY
                                             │
                ┌────────────────────────────┼────────────────────────────┐
                │                            │                            │
                ▼                            ▼                            ▼
    PRISME Binary          ChromaSpeechAI                  Dedicated physical direction
    Extension              node-to-node                    FPGA / optical transport /
    conventional packet    communication layer             spectral-storage engineering
    interoperability       (LAN verified)
    (experimental)                ↓
                           ChromaNeural
                           distributed AI collaboration
                           (workflow verification in progress)
                                                           (physical validation pending)
```

**The distinction matters:** current implementations run on conventional binary CPUs and memory. ChromaPlex and PRISME define logical representations, language tooling, mappings, and software simulations. ChromaSpeechAI demonstrates verified node-to-node communication using those representations. Dedicated optical or FPGA-oriented hardware is a separate engineering direction, not a completed physical result.

---

## ChromaPlex — the foundation

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

---

## From ChromaPlex to PRISME

[**PRISME**](https://github.com/Janus5G/PRISME) carries the colour-channel direction into a five-channel spectral byte mapping.

```text
one byte
  │
  ├── R, G, B, V: four base-4 symbols = 8 payload bits
  └── UV: (R + G + B + V) mod 4 verification value
```

The four visible data channels represent all 256 byte values. UV is a **verification channel**, not a complete arbitrary multi-error ECC by itself. Higher-level error correction remains a separate layer.

### Software evidence

| Evidence | Result | Classification |
| --- | --- | --- |
| All 256 byte values | encode → verify → decode passes | **Software verified** |
| Single-symbol mutation coverage | 3,840 / 3,840 detected | **Software verified** |
| Random reference blocks | 2,560,000 bytes, zero round-trip errors | **Reference implementation** |
| Compiled C reference run | 268,435,456 bytes, zero errors; measured on one host | **Reference benchmark** |
| Five-channel optical medium | physical channel discrimination, timing, energy, temperature | **Physical verification pending** |

The supplied validation reports support the software mapping and verification behaviour. They do **not** validate an optical write/read path, a glass-storage prototype, specialised FPGA performance, or a physical throughput claim.

---

## One foundation — multiple directions

### Conventional-system interoperability

[**PRISME Binary Extension**](https://github.com/Janus5G/PRISME-Binary-Extension) is an additive, experimental packaging branch for conventional systems.

It converts structured data or binary payloads into portable `.prisme` packages and can emit raw binary, manifests, and C/Rust-compatible byte arrays. The package format defines payload type, optional zlib compression, lengths, CRC-32, SHA-256, package ID, timestamp, and JSON manifest metadata.

> Status: **experimental specification; format stability is not guaranteed; production use is not recommended.**

This extension is separate from PRISME's spectral mapping and is not a mandatory runtime dependency for ChromaPlex or PRISME.

### Node and AI communication

**ChromaSpeechAI** is the implemented communication layer for distributed participation between nodes and AI participants using the ChromaPlex/PRISME colour-symbol representation.

| Capability | Status |
| --- | --- |
| ChromaSpeechAI protocol and software communication | **Implemented / software verified** |
| ChromaSpeechAI node-to-node operation over LAN | **LAN verified** |
| Colour-symbol encoding for inter-node messages | **Verified** |
| Symbol verification and error detection in transit | **Verified** |

**ChromaNeural** is the broader distributed problem-solving layer being developed on top of ChromaSpeechAI communication. Its target workflow divides work across multiple nodes, combines partial results, verifies completed work, and enables verified results to become reusable shared knowledge.

| Capability | Verified status |
| --- | --- |
| Distributed collaboration framework | In development |
| Cubic-4 work-division pattern | In development |
| Result combination and verification workflow | In development |
| Persistent verified-result publication | In development |
| Metadata-based discovery of previous work | In development |
| Reuse of previously verified results | In development |

ChromaSpeechAI communication operates reliably over the current LAN build. The full ChromaNeural workflow components are still being completed and verified.

### Dedicated physical direction

The repositories model a longer-term software/hardware co-design direction: specialised processing, optical transport, and spectral or optical storage that could map appropriate parts of the logical representation more directly into physical systems.

Current public evidence supports:

- software compilers, assemblers, virtual machines, simulators, and browser demonstrations;
- reference spectral mapping and verification tests;
- implemented node-to-node communication over standard LAN;
- engineering concepts and simulations for physical direction.

It does **not** yet support claims of physically verified optical storage, FPGA timing closure, measured specialised-hardware throughput, thermal behaviour, or production laser/control performance.

---

## Engineering status

| Capability | Status |
| --- | --- |
| CPL source language and documented subset | **Implemented** |
| CPA instruction layer and validation | **Implemented** |
| CPL → CPA → simulator flow | **Implemented / software tested** |
| Brainfuck → CPA translator | **Implemented** |
| Separate legacy CPL → bytecode → VM path | **Implemented** |
| Cplex desktop editor and Python bridge | **Implemented; early tooling** |
| PRISME 256-byte five-channel mapping | **Software verified** |
| UV single-symbol corruption detection | **Software verified** |
| Reed–Solomon relationship | **Reference/software-level error-handling design** |
| PRISME Binary Extension package format | **Experimental reference implementation** |
| Automatic ChromaPlex → PRISME production pipeline | **Not verified** |
| General existing-language compatibility compiler | **Not verified** |
| ChromaSpeechAI software communication | **Implemented / software verified** |
| ChromaSpeechAI node-to-node LAN communication | **LAN verified** |
| ChromaNeural complete distributed collaboration workflow | **In development** |
| Cubic-4 distributed-work orchestration | **In development** |
| Verified-result publication and persistence | **In development** |
| Metadata-based discovery of previous work | **In development** |
| Reuse of previously verified results | **In development** |
| FPGA / optical / spectral physical implementation | **Engineering direction; physical verification pending** |

---

## Project map

### Foundation

- [**chromaplex-os**](https://github.com/Janus5G/chromaplex-os)  
  CPL, CPA, assembler, sparse 3D crystal simulator, exponent–remainder utilities, browser demos, and tests.

### Compilation and execution

- [**chromaplex-os-compiler**](https://github.com/Janus5G/chromaplex-os-compiler)  
  Parallel CPL compiler, bytecode assembler, VM, simulated crystal storage, and hardware-control abstraction.

### Development tooling

- [**Cplex**](https://github.com/Janus5G/Cplex)  
  Rust/Slint desktop editor that compiles, runs, and builds supported CPL dialects through a JSON-to-Python bridge.

### Spectral data architecture

- [**PRISME**](https://github.com/Janus5G/PRISME)  
  Five-channel R/G/B/V/UV byte mapping, UV verification logic, browser demonstration, tests, and optical-direction simulation material.

### Interoperability

- [**PRISME-Binary-Extension**](https://github.com/Janus5G/PRISME-Binary-Extension)  
  Experimental portable binary packaging for structured data and arbitrary payloads, with manifests and integrity fields.

---

<div align="center">

Sponsorship supports public compilers, simulators, specifications and engineering documentation.  
It does not sell equity, tokens or exclusive rights to public work.

**[github.com/sponsors/Janus5G](https://github.com/sponsors/Janus5G)**

</div>
