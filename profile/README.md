<div align="center">

<img src="assets/banner.svg" alt="Janus — optical datapath, spectral storage, open toolchains" width="100%">

<br>

[![Sponsor](https://img.shields.io/badge/Sponsor-Janus5G-7C5CFF?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/Janus5G)
[![Profile](https://img.shields.io/badge/GitHub-Janus5G-0B1220?style=for-the-badge&logo=github&logoColor=22D3EE)](https://github.com/Janus5G)
[![Site](https://img.shields.io/badge/aagii.net-0B1220?style=for-the-badge&logo=googlechrome&logoColor=F5C14A)](https://www.aagii.net)
[![Location](https://img.shields.io/badge/Denmark-0B1220?style=for-the-badge&logo=openstreetmap&logoColor=34D399)](https://github.com/Janus5G)

**Systems architect and hardware developer.**  
Open work on optical datapath, spectral storage and the compilers that sit on top of them.

</div>

---

### Focus

<table>
<tr>
<td width="20%" valign="top">

**PRISME**

</td>
<td>

Five-channel spectral storage in glass. Ten bits per light pulse, UV error checking, zero power at rest.

</td>
</tr>
<tr>
<td valign="top">

**ChromaPlex**

</td>
<td>

Experimental CPL/CPA instruction set, compiler, assembler and crystal-voxel simulator for colour-channel storage.

</td>
</tr>
<tr>
<td valign="top">

**Toolchain**

</td>
<td>

Linux-first editor, ISO workbench, portable binary interchange and a multi-mode coding agent.

</td>
</tr>
<tr>
<td valign="top">

**ChromaLearn**

</td>
<td>

Open AI learning platform for schools. Teacher control, session privacy, school-chosen model.

</td>
</tr>
</table>

---

### Vision & Roadmap

<p><img src="https://img.shields.io/badge/1%20%7C%200%20rail-6E7681?style=for-the-badge&labelColor=0B1220&color=6E7681" alt="1-0 rail"> <img src="https://img.shields.io/badge/five%20colour%20channels-22D3EE?style=for-the-badge&labelColor=0B1220&color=22D3EE" alt="five colour channels"> <img src="https://img.shields.io/badge/Vision%20%26%20Roadmap-F5C14A?style=for-the-badge&labelColor=0B1220&color=F5C14A" alt="Vision & Roadmap"></p>

<img src="https://raw.githubusercontent.com/Janus5G/.github/main/vision-roadmap.png" alt="Off the 1-0 rail" width="150" align="right">

The inherited computer is a two-state wire: **1** or **0**, then the next bit, then the next. That is the von Neumann neck — sequential tokens, linear tensors, one rail for every thought. It works. It also caps the machine.

**ChromaNeural / Chromaplex** is the path off that rail. A forward-compatible stack that already runs on current CPU/GPU hardware while the optical datapath and spectral storage layer are designed in parallel. Five colour channels, spatial layers, and one software path from editor to compiler to OS — patterns instead of a single-file of bits.

<br clear="all">

The aim is to move past sequential token streams and linear tensor steps toward multidimensional pattern processing: five colour channels, spatial layers, and a software path that stays consistent from editor to compiler to OS.

<table>
<tr>
<td width="20%" valign="top">

**Now**

</td>
<td>

Core neural and software components are implemented and tested on current-generation CPU/GPU machines. Logical structures follow the Chromaplex model; the physical layer is still emulated. No custom FPGA, LPU or optical hardware has been verified yet.

</td>
</tr>
<tr>
<td valign="top">

**Target**

</td>
<td>

Custom hardware in design and blueprint: Lattice ECP5-45F FPGA PCB, dedicated LPU processors, and optical interconnects as the physical unlock for full theoretical performance.

</td>
</tr>
</table>

#### From linear binary to multidimensional patterns

Current architectures are bound by sequential tokenisation and linear tensor work. PRISME (including the binary extension) treats data as light-patterns across five colour channels and spatial layers. On legacy hardware this is emulated; the same logic is intended to map onto the optical medium without rewriting the stack.

#### Hardware plasticity — Lattice FPGA and LPU

The proposed board uses a Lattice ECP5-45F FPGA rather than a fixed ASIC.

- **Physical self-optimisation** — design intent: once the FPGA path exists, the system should be able to redesign its own logical gates at runtime to cut latency. Not implemented in silicon.
- **LPU integration** — blueprint only: a dedicated Language Processing Unit to remove tokenisation overhead.
- **Projected gains (software only)** — **3×** GPU efficiency and **8×** LPU throughput are software-side estimates from tests and modelling on existing CPU/GPU hardware. They are **not hardware-verified**. Target silicon, optical interconnects and fused-silica storage remain in design.

#### Full-stack path: Cplex → compiler → ChromaOS

| Layer | Role |
| --- | --- |
| **Cplex** | High-level language for multidimensional operations |
| **Chromaplex compiler** | Turns Cplex abstractions into PRISME patterns — same logic on legacy silicon or target FPGA |
| **ChromaOS** | OS tuned for neural collaboration. Node-to-node AI communication is implemented and software-verified; the future optical hardware layer remains separate and is not yet physically verified. |

#### Physical layer ahead — optics and fused silica

Blueprints include a move off electrical interconnects to cut interference and wear:

- **Ultra-low latency buffers** — optical fibre spools between GPUs, with UV real-time error correction.
- **Fused silica storage** — five-dimensional nanostructures in quartz glass for long-lived persistence and high optical bandwidth.

ChromaNeural is built as a seamless path: software that works today, hardware that can evolve with the compute model rather than lock it to a rigid ISA.

---

### Repositories

| | Project | Role |
| :---: | --- | --- |
| <img src="https://img.shields.io/badge/·-7C5CFF?style=flat-square"> | [PRISME](https://github.com/Janus5G/PRISME) | Spectral storage, error checking, archival glass medium |
| <img src="https://img.shields.io/badge/·-3B82F6?style=flat-square"> | [chromaplex-os](https://github.com/Janus5G/chromaplex-os) | Language, compiler, assembler, 3D crystal simulator |
| <img src="https://img.shields.io/badge/·-22D3EE?style=flat-square"> | [chromaplex-os-compiler](https://github.com/Janus5G/chromaplex-os-compiler) | Compiler toolchain for ChromaPlex OS |
| <img src="https://img.shields.io/badge/·-34D399?style=flat-square"> | [Cplex](https://github.com/Janus5G/Cplex) | Rust/Slint desktop editor with CPA assembly and simulator |
| <img src="https://img.shields.io/badge/·-F5C14A?style=flat-square"> | [Chromaplex-Coding-Agent](https://github.com/Janus5G/Chromaplex-Coding-Agent) | Multi-mode agent for Linux, Windows, web, embedded, CPL/CPA |
| <img src="https://img.shields.io/badge/·-A78BFA?style=flat-square"> | [ChromaLearn](https://github.com/Janus5G/ChromaLearn) | School AI platform with session-private data |
| | [ChromaPress](https://github.com/Janus5G/ChromaPress) | Linux ISO customisation for WSL2 and Debian/Ubuntu |
| | [PRISME-Binary-Extension](https://github.com/Janus5G/PRISME-Binary-Extension) | Portable binary packaging for edge and server systems |
| | [Architecture spec](https://github.com/Janus5G/ChromaPlex-v2.0-Specification-Architecture-Documentation) | Spatial and angular optical computer architecture |

---

<div align="center">

### Stack

<img src="https://img.shields.io/badge/Python-0B1220?style=flat-square&logo=python&logoColor=22D3EE" alt="Python">
<img src="https://img.shields.io/badge/Rust-0B1220?style=flat-square&logo=rust&logoColor=E8EEF7" alt="Rust">
<img src="https://img.shields.io/badge/CPL%20%2F%20CPA-0B1220?style=flat-square&logoColor=7C5CFF" alt="CPL/CPA">
<img src="https://img.shields.io/badge/Photonics-0B1220?style=flat-square&logoColor=F5C14A" alt="Photonics">
<img src="https://img.shields.io/badge/Linux-0B1220?style=flat-square&logo=linux&logoColor=34D399" alt="Linux">
<img src="https://img.shields.io/badge/Embedded-0B1220?style=flat-square&logoColor=3B82F6" alt="Embedded">

<br><br>

</div>

---

<div align="center">

Sponsorship supports public compilers, simulators, specs and school tooling.  
It does not sell equity, tokens or exclusive rights to the public work.

**[github.com/sponsors/Janus5G](https://github.com/sponsors/Janus5G)**

</div>
