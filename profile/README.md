<div align="center">

<img src="https://raw.githubusercontent.com/datara-lang/.github/main/profile/icon.png" width="130" height="130" alt="Datara Logo" style="border-radius: 20px;" />

# The Datara Programming Language

**Deterministic Systems & Application Language for the Modern Era**

<p>
  <a href="https://github.com/datara-lang/datara"><img src="https://img.shields.io/badge/Language-Datara-E3B341?style=for-the-badge&logo=codeforces&logoColor=white" alt="Datara" /></a>
  <a href="https://github.com/datara-lang/datara"><img src="https://img.shields.io/badge/Memory-Affine_Zero--GC-2563EB?style=for-the-badge&logo=speedtest&logoColor=white" alt="Affine Memory" /></a>
  <a href="https://github.com/datara-lang/datara"><img src="https://img.shields.io/badge/Compiler-Cranelift_%2B_LLVM-10B981?style=for-the-badge&logo=llvm&logoColor=white" alt="Dual Engine Compiler" /></a>
  <a href="https://github.com/datara-lang/sparks"><img src="https://img.shields.io/badge/Packages-Sparks_Ed25519-7C3AED?style=for-the-badge&logo=box&logoColor=white" alt="Sparks Registry" /></a>
  <a href="https://github.com/datara-lang/datara/blob/main/LICENSE-MIT"><img src="https://img.shields.io/badge/License-Apache_2.0_OR_MIT-0EA5E9?style=for-the-badge&logo=open-source-initiative&logoColor=white" alt="License" /></a>
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

Designed specifically for low-latency infrastructure, game engines, high-frequency trading systems, distributed cloud services, and real-time audio/video pipelines, Datara enforces **automatic memory safety at compile time without a garbage collector** and without the steep learning curve of manual lifetime annotations.

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
    total_value() -> Float => this.shares.to_float() * this.price

    format_summary() -> Str {
        return fmt"Order #{this.id}: {this.shares}x {this.symbol} @ ${this.price} (Total: ${this.total_value()})"
    }
}

// Dataflow pipeline transformation
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
Datara tracks resource ownership and lifetimes automatically through static lexical regions. You get the deterministic deallocation guarantees and zero-overhead memory footprint of Rust without writing `'a`, `'b` lifetime sigils.

#### 2. Dual-Engine Compiler Architecture
* **Instant Developer Feedback**: Sub-30ms JIT evaluation and compilation via **Cranelift**.
* **Production Peak Performance**: Whole-program optimization, auto-vectorization, profile-guided optimization (PGO), and link-time optimization via **LLVM AOT (`-O3 -flto`)**.
* **Sandboxed Execution**: Native **WebAssembly (WASM SIMD)** target with capability-guarded execution.

#### 3. Evidence Gate Formal Verification
Every optimization pass in the `forgen` compiler pipeline (SROA, Mem2Reg, Bound-Check Elimination, LoopFold, CSE) produces formal mathematical proofs at the SSA DMIR intermediate representation level. Undefined behavior and out-of-bounds accesses are eliminated by construction.

#### 4. Universal Polyglot Interoperability
Datara directly bridges foreign ecosystems with zero rewrite overhead:
* **C / C++**: Direct header parsing and native dynamic linking without manual glue code.
* **Python**: Direct CPython runtime integration with zero-copy buffer export for NumPy, PyTorch, and SciPy.
* **Rust**: Seamless consumption of crates via C-ABI and automated bindings.
* **Node.js**: Embedded V8/N-API bridging for full package ecosystem access.

#### 5. Allocator Tiers & Systems Control
Fine-grained execution control when standard stack and RAII allocation are not enough:
* `@arena`, `@pool`, and `@heap` scope-level memory management with O(1) bulk destruction.
* Structured inline assembly with two-way variable binding for performance-critical inner loops.
* Amortized O(1) string builder (`StrBuf`) for high-throughput stream processing.

#### 6. Cryptographically Secured Package Ecosystem
The **Sparks** package registry cryptographically signs package manifests using Ed25519 signatures and enforces fine-grained capability descriptors (`.capabilities.json`) to neutralize supply-chain attack vectors.

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
| **Native Multi-Backend (JIT + AOT + WASM)** | Yes | No | No | No |

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
datara info
```

---

<h3 id="ecosystem">Official Organization Repositories</h3>

| Repository | Role & Architecture | Tier | Stack |
|:---|:---|:---:|:---|
| **[datara-lang/datara](https://github.com/datara-lang/datara)** | Core systems language compiler (`forgen`), runtime, SSA DMIR optimizer & stdlib | Core Toolchain | Rust, Cranelift, LLVM, C++ |
| **[datara-lang/sparks](https://github.com/datara-lang/sparks)** | Decentralized cryptographic package manager with Ed25519 capabilities | Ecosystem | Python, Cryptography, Rust |
| **[datara-lang/datara-grammar](https://github.com/datara-lang/datara-grammar)** | Syntax highlighting grammars for VS Code, TextMate, and IDEs | Tooling | TypeScript, JSON, TextMate |

---

<div align="center">
  <sub>Maintained by the Datara Language Project &bull; Licensed under Apache-2.0 / MIT</sub>
</div>
