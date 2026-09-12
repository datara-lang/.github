<div align="center">

<img src="https://raw.githubusercontent.com/datara-lang/.github/main/profile/icon.png" width="130" height="130" alt="Datara Logo" style="border-radius: 20px;" />

# The Datara Programming Language

**Deterministic Systems & Application Language for the Modern Era**

<p>
  <a href="https://github.com/datara-lang/datara"><img src="https://img.shields.io/badge/Language-Datara-E3B341?style=for-the-badge&logo=codeforces&logoColor=white" alt="Datara" /></a>
  <a href="https://github.com/datara-lang/datara/releases"><img src="https://img.shields.io/badge/Version-1.2.0_Apex-2563EB?style=for-the-badge&logo=git&logoColor=white" alt="Version 1.2.0" /></a>
  <a href="https://github.com/datara-lang/datara/blob/main/LICENSE-APACHE"><img src="https://img.shields.io/badge/License-Apache_2.0_OR_MIT-10B981?style=for-the-badge&logo=open-source-initiative&logoColor=white" alt="License" /></a>
  <a href="https://github.com/github-linguist/linguist/pull/8189"><img src="https://img.shields.io/badge/Linguist-PR_%238189-F59E0B?style=for-the-badge&logo=github&logoColor=white" alt="Linguist PR" /></a>
</p>

<p align="center">
  <a href="#quickstart">Quickstart</a> &bull;
  <a href="#code-sample">Code Tour</a> &bull;
  <a href="#core-pillars">Core Pillars</a> &bull;
  <a href="#comparison">Comparison</a> &bull;
  <a href="#ecosystem">Ecosystem</a> &bull;
  <a href="https://github.com/datara-lang/datara/tree/main/docs">Documentation</a>
</p>

</div>

---

### Overview

**Datara** unites the mechanical sympathy and sub-millisecond execution of bare-metal C and Rust with the syntactic elegance and developer velocity of modern languages.

Designed specifically for low-latency infrastructure, game engines, high-frequency systems, and distributed cloud services, Datara enforces **automatic memory safety at compile time without a garbage collector** and without the steep learning curve of manual lifetime annotations.

---

<h3 id="code-sample">Code Tour</h3>

Here is what idiomatic Datara code looks like:

```datara
// Data-oriented record with affine ownership
class Order {
    id: Int
    symbol: Str
    shares: Int
    price: Float
}

// Behavioral extension: methods separated from raw state
behavior Order {
    total_value() -> Float => shares.to_float() * price

    format_summary() -> Str {
        return fmt"Order #{id}: {shares}x {symbol} @ ${price} (Total: ${total_value()})"
    }
}

// Pipeline transformation
fn apply_rebate(val: Float) -> Float => val * 0.98

fn main() {
    let order = Order { id: 2048, symbol: "NVDA", shares: 50, price: 124.50 }

    let final_cost = order.total_value() |> apply_rebate()

    println(order.format_summary())
    println(fmt"Discounted execution cost: ${final_cost}")
}
```

---

<h3 id="core-pillars">Core Pillars</h3>

#### 1. Affine Ownership Without Annotations
Datara tracks resource ownership and lifetimes automatically through static lexical regions. You get the deterministic deallocation guarantees of Rust without writing `'a`, `'b` lifetime sigils.

#### 2. Evidence Gate Optimizer
Every optimization pass in the `forgen` compiler pipeline (SROA, Mem2Reg, BCE, LoopFold, CSE) produces formal mathematical proofs at the SSA DMIR intermediate representation level. Undefined behavior is eliminated by construction.

#### 3. Dual-Engine Compiler
* **Developer Velocity**: Instant 30–50ms JIT evaluation and compilation via **Cranelift**.
* **Production Peak Performance**: Whole-program optimization, auto-vectorization, and profile-guided optimization (PGO) via **LLVM AOT (`-O3 -flto`)**.
* **Zero-Trust Sandboxing**: Native **WebAssembly** target with capability-guarded execution.

#### 4. Cryptographically Secured Package Ecosystem
The **Sparks** package manager cryptographically signs package manifests using Ed25519 keys and enforces fine-grained capability descriptors (`.capabilities.json`) to prevent supply-chain vulnerabilities.

---

<h3 id="comparison">Architectural Comparison</h3>

| Feature | Datara | Rust | C++ | Go |
|:---|:---:|:---:|:---:|:---:|
| **Zero Runtime GC Pauses** | Yes | Yes | Yes | No (Stop-The-World) |
| **No Manual Lifetime Sigils (`'a`)** | Yes | No | Yes (Unsafe) | Yes (GC) |
| **Deterministic IEEE-754 Floating Point** | Yes | No | No | No |
| **Sub-50ms Fast Developer Build Time** | Yes (Cranelift) | No (Slow LLVM) | No | Yes |
| **Evidence Gate Formal Verification** | Yes (DMIR SSA) | No | No | No |
| **Native Dataflow Pipelines (`\|>`)** | Yes | No | No | No |
| **Capability-Guarded Package Sidecars** | Yes (Sparks) | No | No | No |

---

<h3 id="quickstart">Quickstart Installation</h3>

Install the complete Datara toolchain (`forgen` compiler, language server, and `sparks` package manager) with a single command:

#### Windows (PowerShell):
```powershell
irm https://raw.githubusercontent.com/datara-lang/datara/main/install.ps1 | iex
```

#### Linux & macOS (Bash):
```bash
curl -fsSL https://raw.githubusercontent.com/datara-lang/datara/main/install.sh | sh
```

Verify your installation:
```bash
datara version
```

---

<h3 id="ecosystem">Official Organization Repositories</h3>

| Repository | Focus & Role | Version |
|:---|:---|:---:|
| **[datara-lang/datara](https://github.com/datara-lang/datara)** | The core programming language compiler (`forgen`), runtime systems, and standard library. | `v1.2.0` |
| **[datara-lang/sparks](https://github.com/datara-lang/sparks)** | The official cryptographic package registry and dependency manager. | `Active` |
| **[datara-lang/datara-grammar](https://github.com/datara-lang/datara-grammar)** | TextMate and editor syntax highlighting grammar for GitHub and VS Code. | `v1.0.0` |

---

<div align="center">
  <sub>Maintained by the Datara Language Project &bull; Licensed under Apache-2.0 / MIT</sub>
</div>
