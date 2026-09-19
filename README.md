<div id="toc" align="center" style="margin-bottom: 0; padding-bottom: 0;">
  <ul style="list-style: none; margin: 0; padding: 0;">
    <summary>
      <h1 align="center" style="margin: 0; padding: 0;">⋆ aum47's stock roadstr kernels ⋆</h1>
      <p align="center" style="font-size: 9px; color: #777; margin-top: 5px; margin-bottom: 2px;">
        <small>Stability-focused GKI + qcom stock kernel by moto 6.6 kernel for Moto Edge 70 (SM7750)</small>
      </p>
      <p align="center" style="font-size:12px; margin-top: 0; margin-bottom: 20px;">
        <i>ReSukiSU &amp; KernelSU Next &amp; KernelSU &amp; SukiSU Ultra</i>
      </p>
    </summary>
  </ul>
</div>

<p align="center">
  <a href="#-features"><img src="https://img.shields.io/badge/Features-20+-brightgreen?style=flat-square" /></a>
  <a href="#-build-workflow"><img src="https://img.shields.io/badge/Build-GitHub_Actions-blue?style=flat-square" /></a>
  <a href="#-memory--scheduler-optimizations"><img src="https://img.shields.io/badge/Optimizations-24_patches-purple?style=flat-square" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/palazik/actions_oplus_sm8750?style=flat-square" /></a>
</p>

---

## ⚙️ Kernel Information

| Property | Value |
|----------|-------|
| **Kernel Version** | `6.6.143` (upstreamed from Qcom-GKI 6.6.89) |
| **Chipset** | `SM7750` \| Snapdragon 7 Gen 4 \| sun |
| **Android Version** | `16-17?` (compatible with later versions) |
| **ROM Compatibility** |stock helloui. idk about los|
| **Root Solution** | ReSukiSU / KSU Next / KSU / SukiSU Ultra |
| **Build System** | GitHub Actions CI/CD (optimized for ~5-6min builds) |

---

## 🎯 ROM Compatibility
yes
---

## 📝 Features

### 🔁 Kernel Version
- ✅ **Upstream** – Upstreaming the OnePlus's official kernel to the Google's newest A15 6.6 kernel

### 🔐 Security & Hide
- ✅ **SuSFS** – Enhanced environment hiding (path/mount/kstat spoofing)
- ✅ **Baseband Guard** – Anti-brick modem protection
- ✅ **Unicode Bypass Fix** – Path traversal protection *(always on)*

### 🚀 Performance & Scheduler
- TO BE REMOVED **Fengchi / HMBIRD** – Advanced CPU scheduler optimizations for SM8750 *(turning it off also removes HMBIRD symbols that some OnePlus vendor modules may use)*
- ✅ **BORE Scheduler** – Burst-Oriented Response Enhancer (EEVDF) for snappier interactivity *(optional, off by default)*
- ✅ **ADIOS IO Scheduler** – Improved read/write performance
- ✅ **Oryon CPU Tuning** – `-mcpu=oryon-1` flags for SM8750

### 🌐 Networking
- ✅ **TCP BBR + Brutal** – Modern congestion control algorithms
- ✅ **BBRv3** – Google's latest TCP congestion control, backported to 6.6
- ✅ **WireGuard** – Kernel-level VPN support
- ✅ **Full Netfilter** – Conntrack, NAT, hashlimit *(optional)*
- ✅ **IP_SET + IPv6 NAT** – Advanced firewall + IPv6 masquerade *(optional)*
- ✅ **TTL/HL Target** – Hide tethering from carrier detection *(optional)*

### 💾 Storage & Memory
- ✅ **LZ4 1.10.0 + ZSTD 1.5.7** – Faster compression for ZRAM
- ✅ **LZ4KD** – Kernel-level ZRAM optimization *(optional)*
- ✅ **ZRAM Writeback** – Better memory management *(optional)*
- ✅ **F2FS Optimizations** – Enhanced flash storage performance *(optional)*

### 🎮 Gaming & Compatibility
- ✅ **NTSync** – Low-latency NT sync primitives (Wine/Proton gaming) *(optional)*
- ✅ **Droidspaces** – SYSVIPC + PID_NS + POSIX_MQUEUE for proot-distro
- ✅ **LRNG v60** – Better entropy for crypto/gaming *(optional)*

### 🔋 Battery & Power
- ✅ **Wakelock Blocker** – Reduce idle battery drain
- ✅ **Re-Kernel Support** – Enhanced app freezing via NoActive/Freezer *(optional)*

### 🧩 KernelSU Enhancements
- ✅ **Multi-Manager** – Compatible with multiple KSU variants

---

## 🧠 Memory & Scheduler Optimizations (WildKernels)

> 24 low-level patches for reduced latency, better cache usage, and improved responsiveness.

| Patch | Purpose |
|-------|---------|
| `optimized_mem_operations.patch` | Optimized memcpy/memset for ARM64 |
| `file_struct_8bytes_align.patch` | Align file structures for better cache locality |
| `reduce_cache_pressure.patch` | Lower memory pressure during heavy workloads |
| `mem_opt_prefetch.patch` | Smart prefetching for sequential access patterns |
| `optimise_memcmp.patch` | Faster memory comparison routines |
| `minimise_wakeup_time.patch` | Reduce CPU wake latency for interactive tasks |
| `int_sqrt.patch` | Optimized integer square root for scheduler math |
| `reduce_gc_thread_sleep_time.patch` | Shorter GC thread sleeps for smoother UI |
| `add_timeout_wakelocks_globally.patch` | Prevent aggressive wakelock timeouts |
| `f2fs_reduce_congestion.patch` | Lower F2FS write contention |
| `reduce_freeze_timeout.patch` | Faster app freeze/unfreeze transitions |
| `clear_page_16bytes_align.patch` | 16-byte aligned page clearing for NEON efficiency |
| `add_limitation_scaling_min_freq.patch` | Smarter min-frequency scaling limits |
| `re_write_limitation_scaling_min_freq.patch` | Refined frequency scaling behavior |
| `adjust_cpu_scan_order.patch` | Optimized CPU selection order for task placement |
| `avoid_extra_s2idle_wake_attempts.patch` | Reduce unnecessary suspend-to-idle wakes |
| `disable_cache_hot_buddy.patch` | Prevent cache thrashing in buddy allocator |
| `f2fs_enlarge_min_fsync_blocks.patch` | Larger fsync batches for F2FS efficiency |
| `increase_ext4_default_commit_age.patch` | Less frequent EXT4 journal commits |
| `increase_sk_mem_packets.patch` | Larger socket buffer for high-throughput networking |
| `reduce_pci_pme_wakeups.patch` | Fewer PCIe power management wakeups |
| `silence_irq_cpu_logspam.patch` | Reduce IRQ-related kernel log noise |
| `silence_system_logspam.patch` | Cleaner dmesg output |
| `use_unlikely_wrap_cpufreq.patch` | Branch prediction hints for cpufreq paths |

---

## 🤖 Compiler & Build Configuration

### Toolchain
- **Clang**: ZyCromerZ Clang 19.0.0git, Oryon-optimized (ColorOS/OxygenOS) — or AOSP Clang `clang-r563880c` for AOSP builds
- **Linker**: LLD 19 with ThinLTO cache in `$GITHUB_WORKSPACE`
- **CCache**: ECS-enhanced ccache with 10GB cache + aggressive sloppiness

### Compiler Flags
```bash
-O2                          # Balanced optimization level
-mcpu=oryon-1               # Target Snapdragon 8 Elite cores
-flto=thin                  # ThinLTO for link-time optimization (optional)
-ffile-prefix-map=...       # Reproducible builds
```


## 📱 Supported Devices

| Device | Codename | Status |
|--------|----------|--------|
| **Moto Edge 70** |roadstr|yes| 

> Requires unlocked bootloader + custom recovery (TWRP / KernelFlasher)

---

## 📦 Installation

1. Download the latest `AnyKernel3_*.zip`:
2. Boot to custom recovery IF EXISTS (TWRP / OrangeFox / KernelFlasher)
3. Flash the AnyKernel3 ZIP
4. **(Required)** Install a metamodule for KSU:
   - [mountify](https://github.com/SukiSU-Ultra/mountify)
   - [meta-overlayfs](https://github.com/SukiSU-Ultra/meta-overlayfs)
   - [meta-magicmount](https://github.com/SukiSU-Ultra/meta-magicmount)
5. Reboot and enjoy! 🎉

> ⚠️ **Disclaimer**: I am not responsible for bricked devices, data loss, or other issues. Flash at your own risk.

---

## 🤝 Credits & Acknowledgements

| Contributor | Contribution |
|-------------|-------------|
| [mrcxlinux](https://github.com/mrcxlinux) | The base workflow
| [xiaomichael](https://github.com/xiaomichael) | Some help & GKI infrastructure |
| [cctv18](https://github.com/cctv18) | Base of kernel source, ccache-ESC |
| [Numbersf](https://github.com/Numbersf) | Fengchi / HMBIRD scheduler patches |
| [ShirkNeko](https://github.com/ShirkNeko) | LZ4KD & ZRAM patches |
| [ZyCromerZ](https://github.com/ZyCromerZ) | Oryon-optimized Clang 19 toolchain |
| [linx3141](https://github.com/linx3141) | AOSP support |
| [TheWildJames](https://github.com/TheWildJames) | Unicode fix & additional kernel patches |
| [FatalCoder524](https://github.com/fatalcoder524) | BBRv3, kernel optimization patches |
| [brokestar233](https://github.com/brokestar233) | BORE scheduler integration for OnePlus SM8750 (source patch) |
| [firelzrd](https://github.com/firelzrd) | BORE (Burst-Oriented Response Enhancer) CPU scheduler |



<p align="center">
  <sub>Built by aum47 with help of palaziks • Kernel version: <code>6.6.143-aum47-SkyKenrel</code></sub>
</p>
