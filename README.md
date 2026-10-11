<div align="center">
  <img width="160" src="./resources/img/materialHacker.png" alt="Execorn avatar" style="border-radius: 50%;" />
  <h1>Nikita Biryukov</h1>
  <p>
    Quant Developer at <strong>Sberbank CIB</strong> (Global Markets) &middot; Master's student at <strong>MIPT</strong> (Quant Finance)
  </p>
  <p>
    <a href="https://t.me/execorn"><img src="https://img.shields.io/badge/Telegram-@execorn-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Telegram"/></a>
    <a href="mailto:n.biryukov.04@gmail.com"><img src="https://img.shields.io/badge/Email-n.biryukov.04@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email"/></a>
    <a href="https://github.com/Execorn"><img src="https://img.shields.io/badge/GitHub-Execorn-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"/></a>
    <img src="https://img.shields.io/badge/OS-Arch%20Linux-1793D1?style=flat-square&logo=arch-linux&logoColor=white" alt="Arch Linux"/>
  </p>
</div>

---

Most of my time goes into two things: shaving latency off derivatives risk engines at Sberbank CIB, and building Linux software that talks straight to the hardware.

By day, I work on C++ adapters and calculation pipelines for Rates, FX, and Equity derivatives. We are moving pricing and risk out of legacy Murex monoliths into an in-house calculation service. That means zero-copy data mapping, streaming market data, Greeks injection, and Monte Carlo scenarios for XVA.

On weekends, I write Wayland daemons in C23, benchmark SIMD routines, and train neural operators on GPUs.

- **Work:** Middle Quant Developer at Sberbank CIB (Global Markets / ДГР)
- **Education:** MIPT ФПМИ &mdash; BSc in CS ('25), MSc in Corporate Strategy & Quant Finance ('26), with ML coursework from Yandex School of Data Analysis (ШАД)
- **Setup:** Arch Linux, Hyprland, pure terminal workflow, Neovim

---

### What I Build

#### [derivatives](https://github.com/Execorn/derivatives) &mdash; GPU rough volatility calibration and structured derivatives engine
An institutional quantitative derivatives platform built for my master's thesis at MIPT, covering a 16-model zoo from rough volatility to multi-asset structured products. It pairs FiLM-conditioned Fourier Neural Operators (FNO) pricing 8×11 rough Heston surfaces in <1 ms ($R^2 = 0.9991$, MAE = 5.8 bp, 1400× speedup over Fourier-COS) with a multi-fidelity autocallable engine (Crank-Nicolson PDE base + 5-member residual MLP ensemble delivering 0.99 bp RMSE and SR 26-2 risk rejection). Also features Equivariant Graph Neural Operators (EGNO) for Worst-Of basket notes, recurrent deep hedging, and a GPU Monte Carlo risk engine evaluating $10^7$ portfolio revaluations per second. High-throughput FastAPI streaming (353 RPS) backed by 1,126 passing tests.

#### [wwal](https://github.com/Execorn/wwal) &mdash; Zero-allocation Wayland wallpaper daemon
Most animated wallpaper tools on Linux eat GPU power or drop frames during workspace transitions. `wwal` is written in modern C (C23). It uses direct hardware scanout via `dmabuf` and GBM overlay planes, which drops GPU 3D load to 0.0%. For video, it decodes via VA-API straight into DRM PRIME buffers (&lt;0.5% CPU at 4K 60fps). The event loop runs on Linux `io_uring` and a fixed 2MB bump allocator that never touches the heap at runtime.

#### [Fast-hash-table](https://github.com/Execorn/Fast-hash-table) &mdash; AVX2 SIMD hash table
A closed-addressing hash table in C aligned to hardware cache lines. Uses 256-bit AVX2 intrinsics (`_mm256_cmpeq_epi8`) to compare 32 keys in parallel in a single cycle, with hardware CRC32 (`_mm_crc32_u64`).

#### [aurora-greeter](https://github.com/Execorn/aurora-greeter) &mdash; Hardware-adaptive SDDM login theme
An SDDM theme for Arch Linux with video backdrops, packaged on the AUR. Includes an in-greeter settings drawer (`Alt+S`) so you never have to edit config files by hand, plus automatic 4K &rarr; 2K downscaling on smaller screens.

#### [HyprGlyph](https://github.com/Execorn/HyprGlyph) &mdash; Hyprland keybinding parser
Instead of maintaining duplicate cheatsheet tables that go stale every time you edit your window manager config, this parses bindings directly from your Hyprland files into structured JSON for desktop overlay drawers. Written in Python, 67 passed tests.

#### [Execore_Language](https://github.com/Execorn/Execore_Language) &mdash; Statically typed language engine in ISO C++23
An interpreted language runtime combining Python-style indentation syntax with explicit static types (`int`, `float`, `char`, `str`, `list`), first-class lexical closures, and runtime method dispatch. Engineered for cache locality and zero-allocation execution paths: tokens stream through Structure-of-Arrays buffers (`TokenBufferSoA`) for 100% L1 cache density, AST nodes allocate from PMR monotonic memory arenas (`std::pmr`), and errors propagate via C++23 `std::expected` monadic chaining. Tagged `std::variant` primitives evaluate without heap hits. Passes a 5-tier test matrix (unit, BDD, 2,000 property tests, LibFuzzer, mutation testing) and achieves >100 MiB/s lexer throughput (~4.8M tokens/s) under PGO and ThinLTO.

---

### Stack

- **Systems & Low-Latency:** Modern C++ (17/20/23), Modern C (C23), x86-64 NASM Assembly, AVX2 SIMD, Linux `io_uring`, DMA-BUF, DRM/GBM, Wayland protocols, POSIX.
- **Quant & ML:** Rough volatility, Black-Scholes, Greeks (Δ, Γ, ν), XVA (CVA, PFE), Fourier Neural Operators (FNO), Equivariant GNOs, Multi-Fidelity PDE Ensembles, PyTorch, CUDA, TensorRT, Murex FLEX API.
- **Environment:** Arch Linux, Hyprland, Meson, CMake, Git, Docker, Go, Python.

---

<div align="center">
  <p><em>"Premature optimization is the root of all evil &mdash; unless you are out of clock cycles before the market moves."</em></p>
  <p><sub>Telegram: <a href="https://t.me/execorn">@execorn</a> &middot; <a href="mailto:n.biryukov.04@gmail.com">n.biryukov.04@gmail.com</a> &middot; Moscow, Russia</sub></p>
</div>
