# The Datara Programming Language

<p align="center">
  <b>A next-generation compiled systems language engineered for mechanical sympathy, affine ownership without annotations, zero-GC predictability, and bare-metal execution speed.</b>
</p>

<p align="center">
  <a href="https://github.com/datara-lang/datara"><img src="https://img.shields.io/badge/Language-Datara-%23E3B341?style=for-the-badge&logoColor=white" alt="Datara"></a>
  <a href="https://github.com/datara-lang/datara/releases"><img src="https://img.shields.io/badge/Version-1.2.0_Apex-blue?style=for-the-badge" alt="Version 1.2.0"></a>
  <a href="https://github.com/datara-lang/datara/blob/main/LICENSE-APACHE"><img src="https://img.shields.io/badge/License-Apache_2.0_OR_MIT-green?style=for-the-badge" alt="License"></a>
  <a href="https://github.com/github-linguist/linguist/pull/8189"><img src="https://img.shields.io/badge/Linguist-PR_%238189-orange?style=for-the-badge" alt="Linguist PR"></a>
</p>

---

### 🏛️ Official Organization Repositories

| Repository | Description | Status |
|---|---|---|
| ⚡ **[`datara-lang/datara`](https://github.com/datara-lang/datara)** | The core Datara programming language compiler toolchain (`forgen`), runtime, standard library, and verification test suites. | Production v1.2.0 |
| 📦 **[`datara-lang/sparks`](https://github.com/datara-lang/sparks)** | The official cryptographic package manager and package registry for Datara libraries and frameworks. | Active |
| 🎨 **[`datara-lang/datara-grammar`](https://github.com/datara-lang/datara-grammar)** | TextMate and editor syntax highlighting grammar for `.dtr` files (powers GitHub and VS Code highlighting). | v1.0.0 |

---

### ⚡ Key Architectural Pillars

* **Affine Ownership Without Annotations**: Automatic compile-time memory management with zero GC pauses, zero reference cycles, and zero manual lifetime sigils (`'a`).
* **Evidence Gate Optimizer**: Formal structural mathematical verification at the SSA DMIR intermediate representation level.
* **Deterministic Bit-Exact Compilation**: IEEE-754 identity determinism across runs, reproducible builds, and predictable hardware performance.
* **Industrial Multi-Backend**: Instant 30–50ms developer builds with Cranelift, production peak throughput with LLVM AOT (`-O3 -flto`), and sandboxed browser/cloud execution with WebAssembly.

---

<p align="center">
  <sub>Built with precision by the Datara community • <a href="https://github.com/datara-lang/datara">Explore the documentation →</a></sub>
</p>
