<div align="center">
  <img width="180" src="./resources/img/materialHacker.png" alt="Execorn Hacker Avatar" style="border-radius: 50%;" />
  <h1>Nikita Biryukov</h1>
  <p>
    <strong>Middle Quant Developer @ Sberbank CIB (Global Markets)</strong> · <strong>MIPT ФПМИ (Quant Finance)</strong>
  </p>
  <p>
    <em>Low-latency systems engineering and mathematical finance.</em>
  </p>
  <p>
    <a href="https://t.me/execorn"><img src="https://img.shields.io/badge/Telegram-@execorn-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Telegram"/></a>
    <a href="mailto:n.biryukov.04@gmail.com"><img src="https://img.shields.io/badge/Email-n.biryukov.04@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email"/></a>
    <a href="https://github.com/Execorn"><img src="https://img.shields.io/badge/GitHub-Execorn-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"/></a>
    <img src="https://img.shields.io/badge/OS-Arch%20Linux-1793D1?style=flat-square&logo=arch-linux&logoColor=white" alt="Arch Linux"/>
  </p>
</div>

---

### ⚡ The Snapshot

I spend my working hours cutting latency out of derivatives valuation engines and training neural surrogates on GPUs for rough stochastic volatility. On weekends, I write zero-allocation Wayland engines in C23 and hack on Linux desktop tools.

- 🏛️ **Quant Dev @ Sberbank CIB (Global Markets / ДГР)**: Moving derivatives pricing and risk calculations (Rates, FX, Equity) out of legacy Murex stacks into an in-house low-latency calculation core. Built zero-copy C++ FLEX API adapters, market data feeds (yield curves, vol surfaces), Greeks injection, and XVA (CVA, PFE) Monte Carlo scenario processing.
- 🎓 **MIPT ФПМИ**: Bachelor's in CS ('25) → Master's in Corporate Strategy & Quantitative Finance ('26) with machine learning coursework from Yandex School of Data Analysis (ШАД).
- 🐧 **Environment**: Arch Linux, Wayland/Hyprland, pure CLI, Neovim. If an engine churns heap memory in the hot path or drops frames on a 165Hz VRR panel, it gets rewritten.

---

### 🔬 Selected Projects & Code

<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/Execorn/derivatives">DeepVol: Neural Volatility Engine</a></h3>
      <p><em>Master's Thesis · MIPT ФПМИ (2026)</em></p>
      <p>Real-time calibration of the <strong>Rough Heston stochastic volatility model</strong> on GPUs using Fourier Neural Operators (FiLM-FNO).</p>
      <ul>
        <li><strong>&lt; 1 ms</strong> surface evaluation, replacing multi-second numerical PDE solvers.</li>
        <li><strong>R² = 0.9991</strong>, MAE = <strong>5.8 bp</strong> across deep out-of-the-money options.</li>
        <li>Compiled to <strong>TensorRT FP16</strong> + custom CUDA C++ kernels; 1000+ tests and an interactive Streamlit risk dashboard.</li>
      </ul>
      <p>
        <img src="https://img.shields.io/badge/PyTorch-2.8-EE4C2C?style=flat-square&logo=pytorch&logoColor=white"/>
        <img src="https://img.shields.io/badge/CUDA-12.8-76B900?style=flat-square&logo=nvidia&logoColor=white"/>
        <img src="https://img.shields.io/badge/TensorRT-Engine-76B900?style=flat-square"/>
      </p>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/Execorn/wwal">WayWal: C23 Wayland Engine</a></h3>
      <p><em>Hardware-Limit Linux Graphics Architecture</em></p>
      <p>Zero-allocation Wayland wallpaper daemon (<code>wwald</code>) and CLI client in modern C (C23).</p>
      <ul>
        <li><strong>0.0% GPU 3D Load</strong> using direct hardware scanout (<code>zwp_linux_dmabuf_v1</code> + GBM overlay planes).</li>
        <li><strong>&lt; 0.5% CPU @ 4K 60fps</strong> with VA-API hardware decoding straight into DRM PRIME buffers.</li>
        <li><strong>Sub-50 µs VBlank phase jitter</strong> on VRR displays (FreeSync/G-Sync) with an alpha-beta Phase-Locked Loop (PLL).</li>
        <li>Fixed 2MB linear memory arena: <strong>zero runtime heap allocations</strong> in the event loop. Linux <code>io_uring</code> async kernel ring.</li>
      </ul>
      <p>
        <img src="https://img.shields.io/badge/C-C23-00599C?style=flat-square&logo=c&logoColor=white"/>
        <img src="https://img.shields.io/badge/Linux-io__uring-FCC624?style=flat-square&logo=linux&logoColor=black"/>
        <img src="https://img.shields.io/badge/Wayland-DMA--BUF-blue?style=flat-square"/>
      </p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/Execorn/Fast-hash-table">AVX2 SIMD Hash Table</a></h3>
      <p><em>Vectorized Closed-Addressing Hash Structure</em></p>
      <p>Low-latency hash table aligned to hardware cache boundaries.</p>
      <ul>
        <li>Vectorized lookup comparing <strong>32 keys simultaneously</strong> per cycle using Intel <code>AVX2</code> intrinsics (<code>_mm256_cmpeq_epi8</code>).</li>
        <li>Hardware-accelerated CRC32 hash calculation (<code>_mm_crc32_u64</code>).</li>
        <li>Explicit cache-line memory alignment to prevent splits and false sharing.</li>
      </ul>
      <p>
        <img src="https://img.shields.io/badge/C-AVX2%20Intrinsics-00599C?style=flat-square"/>
        <img src="https://img.shields.io/badge/Assembly-x86--64-yellow?style=flat-square"/>
      </p>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/Execorn/aurora-greeter">Aurora Greeter</a></h3>
      <p><em>Hardware-Adaptive SDDM Login Theme</em></p>
      <p>SDDM login theme for Arch Linux, published on the Arch User Repository (AUR).</p>
      <ul>
        <li>Live in-greeter configuration drawer (<code>Alt+S</code>) without touching raw config files.</li>
        <li>Runtime performance profiles with automatic 4K → 2K URL downscaling on smaller displays.</li>
        <li>Multi-monitor synchronized state machine and CLI companion (<code>sddm-aurora-ctl</code>).</li>
      </ul>
      <p>
        <img src="https://img.shields.io/badge/AUR-sddm--theme--aurora--greeter-1793D1?style=flat-square&logo=arch-linux&logoColor=white"/>
        <img src="https://img.shields.io/badge/Qt-6%20%2F%20QML-41CD52?style=flat-square&logo=qt&logoColor=white"/>
      </p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/Execorn/HyprGlyph">HyprGlyph</a></h3>
      <p><em>Hyprland AST Keybinding Engine</em></p>
      <p>Automated parser and cheatsheet generator for the Hyprland compositor.</p>
      <ul>
        <li>Reads keybindings directly from config files, resolving variables, submaps, and dispatchers.</li>
        <li>Outputs structured JSON schema ready to feed desktop UI drawers (QML, AGS, Eww).</li>
        <li>Tested with a full suite of <strong>67 passed unit tests</strong>.</li>
      </ul>
      <p>
        <img src="https://img.shields.io/badge/Python-3.11-3776AB?style=flat-square&logo=python&logoColor=white"/>
        <img src="https://img.shields.io/badge/Hyprland-Wayland-00B4D8?style=flat-square"/>
      </p>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/Execorn/Execore_Language">Execore Compiler</a></h3>
      <p><em>Domain-Specific Language Built from Scratch</em></p>
      <p>A compiled language demonstrating compiler frontend and runtime mechanics in C.</p>
      <ul>
        <li>Recursive descent parser built on strict EBNF grammar rules.</li>
        <li>Custom Abstract Syntax Tree (AST) construction, memory handling, and execution runtime.</li>
      </ul>
      <p>
        <img src="https://img.shields.io/badge/C-Compiler%20Core-00599C?style=flat-square"/>
        <img src="https://img.shields.io/badge/Grammar-EBNF%20%2F%20AST-orange?style=flat-square"/>
      </p>
    </td>
  </tr>
</table>

---

### 🛠️ Technical Arsenal

```text
Low-Latency & Systems     :: Modern C++ (17/20), Modern C (C23), x86-64 NASM Assembly, SIMD (AVX2/SSE4.2)
Linux Kernel & Plumbing   :: io_uring, zwp_linux_dmabuf_v1, DRM PRIME, GBM overlays, Wayland Protocols, POSIX
Quant & Scientific ML     :: Stochastic Volatility (Rough Heston), Greeks (Δ, Γ, ν), XVA (CVA, PFE), FiLM-FNO
Compute Acceleration      :: PyTorch, CUDA, TensorRT, Zero-Copy Memory Arenas, Cache Optimization
Financial Ecosystem       :: Murex FLEX API (MX.3), Yield Curves, Volatility Surfaces, Monte Carlo Netting
Platform & Tooling        :: Arch Linux, Meson, CMake, Git, Docker, Go, Python, Qt6/QML
```

---

<div align="center">
  <img width="360" src="./resources/img/avento.gif" alt="Avento Pixel Art"/>
  <br/>
  <samp>
    <em>"Premature optimization is the root of all evil — unless you are running out of clock cycles before the market moves or dropping frames on a refresh boundary."</em>
  </samp>
</div>

<br/>

<div align="center">
  <sub>Let's connect: <a href="https://t.me/execorn">Telegram: @execorn</a> · <a href="mailto:n.biryukov.04@gmail.com">n.biryukov.04@gmail.com</a> · Moscow, Russia</sub>
</div>
