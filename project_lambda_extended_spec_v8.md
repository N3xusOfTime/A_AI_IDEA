# Project Lambda: Extended Decentralized Sourcing & Resource Scheduling Specification
**Document ID:** SPEC-EXT-08  
**Author:** Austin Farris Lester  
**License:** Public Domain / Open Source  

---

Ideas compiled through an LLM based entirely on my open-source frameworks. Free to use, modify, append, share, and distribute.

## 1. Decentralized Compute Foundations & Historical Precedent

The scaling mechanics of the system's distributed calculations bypass standard cloud infrastructure limitations by treating high-volume consumer hardware arrays as asynchronous processing cells.

*   **The PS3 Model Precedent:** The framework relies on the historical architecture of early-2000s distributed compute grids, specifically the *Folding@home* protein sequencing matrix deployed across PlayStation 3 clusters and the US Air Force's "Condor Cluster." These precedents proved that complex mathematical workloads can be successfully batched and processed across volatile, residential client infrastructure.
*   **Asynchronous Math Scoping:** Calculations are decoupled from real-time streaming or low-latency network dependencies. Nodes independently download an isolated simulation chunk, compute the payload locally, and return the cryptographic matrix upon completion.

---

## 2. Dynamic Resource Budgeting & Behavioral Profiling Engine

To prevent system lag and ensure the local user retains absolute hardware priority on their system, the computing container rejects static allocation caps in favor of a behavior-aware scheduling engine.

```
┌────────────────────────────────────────────────────────┐
│  TOTAL AVAILABLE SYSTEM HARDWARE (CPU / GPU / RAM)     │
├───────────────────────────┬────────────────────────────┤
│  User Peak Workspace      │Container Dynamic Allocation│
│  (Browsers, Streams, etc.)│  (Scales to zero on spike) │
└────────────────────────────────────────────────────────┘
```

### 2.1 The Pre-Flight Resource Questionnaire
During initial container or daemon activation, the client framework maps the user's typical daily driving baseline through a localized utility prompt:
1.  **Usage Profile Selection:** The user selects their general machine utilization tier (e.g., *Light Web Browsing, Heavy Multitasking, Local Video Streaming / Editing*).
2.  **Peak Task Identification:** The user inputs or benchmarks their peak resource requirements for daily tasks. The system utilizes this input to build a permanent hardware reservation window (e.g., locking out a static 3GB of RAM and 15% CPU headroom specifically to shield browser tabs and media players from computation overhead).

### 2.2 Proportional Allocation & Real-Time Evacuation
The container scales its processing footprint fluidly using a proportional overhead calculation loop:

$$\text{Container Allocation} = \text{Total System Hardware} - (\text{User Peak Baseline} + \text{Active Lifecycle Hooks})$$

*   **Real-Time Thread Yielding:** The container monitors system-wide process telemetry. If an unlisted user application spikes or a video stream launches, the container instantly triggers a memory compaction routine and yields CPU/GPU threads back to the host system within milliseconds.
*   **The Manual Kill-Switch:** The client UI exposes a prominent, global On/Off toggle directly within the desktop environment or gaming overlay (e.g., system tray icon, Steam Quick Access widget). Toggling the switch to "Off" sends an immediate `SIGSTOP` or full container teardown command, completely evacuating the daemon's footprint from system RAM and VRAM.

### 2.3 Automated Game Launcher & Application Hooks
To eliminate manual configuration requirements, the dynamic resource scheduler integrates native process detection hooks targeting primary gaming execution layouts.
*   **Out-of-the-Box Exception Mappings:** The background service monitors the process execution tree. Automated triggers are pre-mapped to primary gaming environments, including **Steam**, **Prism Launcher**, and **ATLauncher**.
*   **Active Game Detection:** The moment an active game process spawns from an exception-mapped launcher, the container pauses calculation workloads instantly.
*   **Active VRAM Flash & Purge Memory Layer:** Before handing control over to the game process, the container executes a hard memory compaction and VRAM purge command (`cudaMemSet` / `vulkan-clear` or full heap deallocation). This completely flushes the container's footprints from the GPU frame buffer and system memory registers *before* the game engine initializes, preventing desktop stutters, frame drops, or Out-of-Memory (OOM) collision crashes. The container remains suspended in this state for the entire duration of the game process lifecycle.
*   **User-Defined Manual Exception Arrays:** Users can register custom binary execution paths via a clean config parameter array (`/etc/lambda/exceptions.conf`), enabling manual override behavior for non-standard software suites or localized rendering pipelines.

---

## 3. File System Architecture: Immutability with Modular Mutability

To maintain a zero-write kernel execution environment while retaining system extensibility, the core architecture implements a multi-layered, hardware-isolated file system matrix.

```
┌──────────────────────────────────────────────────────────┐
│             Mutable Runtime Overlay (RAM Disk)           │  <-- Volatile, wiped on reset
├──────────────────────────────────────────────────────────┤
│   Hardware-Locked Read-Only Modules (Ext. Drive Bays)    │  <-- Additional tools/defensive definitions
├──────────────────────────────────────────────────────────┤
│       Static Base OS Kernel (Internal WORM Media)        │  <-- Hardwired Apollo AGC Core Rope Model
└──────────────────────────────────────────────────────────┘
```

### 3.1 Layered Overlay Framework
*   **The Root Layer (Static WORM Core):** Inspired directly by the Apollo Guidance Computer (AGC) "core rope memory," the primary operating system directories (`/boot`, `/sbin`, `/lib`) reside exclusively on internal, hardware-locked WORM substrate, completely unmodifiable by software commands.
*   **The Modular Extension Layer (Read-Only Expansion Drive Bays):** System updates, upgraded defensive models, and secondary functional modules are deployed via external physical drive slots configured as hardware read-only media. Upon system boot, these expansion blocks map over the base system as stacked, immutable filesystem layers (`overlayfs`).
*   **The Ephemeral State Layer (Volatile Overlay):** Minor runtime parameters and sandboxed workspaces execute entirely within a volatile, temporary memory space (`tmpfs` / RAM disk) that completely collapses during power cycles, clearing all operational footprints.

---

## 4. Cryptographic Verification, Anti-Poisoning, & Performance Protection

Because public distributed processing introduces the risk of targeted data tampering, malicious spoofing, or local thermal and network exhaustion, the central core implements a strict verification and traffic-shaping layer.

### 4.1 Cryptographic Integrity & Input Verification Engine
To eliminate trust boundaries, prevent automated badge exploitation, and maintain core processing performance without complex anti-cheat overhead:
1.  **SHA-256 Verification Loop:** Every discrete calculation block dispatched to the network is cryptographically tagged by the primary Antarctic core. Returning datasets must provide a precisely matching SHA-256 hash output generated directly from the completed matrix. If the returning payload hash deviates by even a single character, the data is instantly discarded.
2.  **Telemetry Validation Constraints:** Mirroring the validated parameters of *Folding@home*, if the received computational data does not structurally relate to the original sent payload properties, the operation is discounted from the verification pool entirely.
3.  **Non-Critical Workload Boundaries:** Distributed consumer infrastructure is strictly banned from handling critical, foundational core operational logic. Instead, the decentralized matrix handles exclusively **sandboxed penetration telemetry and adversarial scenario mapping**. If a node returns corrupted, poisoned, or timed-out calculations, it introduces zero systemic instability to the core.

### 4.2 Fragmented Traffic Shaping & ISP Throttling Guardrails
To prevent Internet Service Providers from identifying, shaping, or throttling container data as heavy peer-to-peer (P2P) or torrent traffic:
1.  **Bifurcated Chunk Scoping:** Massive computational matrices are fractured into micro-chunk packages before distribution.
2.  **Asymmetric Packet Compression:** Data payloads are compressed via low-overhead algorithms and requested in bits and pieces backwards through the network layer, preventing steady high-throughput bandwidth saturation.
3.  **Encapsulated TCP Architecture:** The network strictly avoids peer-to-peer routing protocols. Nodes connect exclusively to a centralized, distributed DNS address over standard TCP ports (e.g., Port 443). By utilizing native TLS/HTTPS encapsulation, the container's traffic mimics standard secure web browser interactions, scrambling the payload signatures from ISP traffic-shaping filters.

### 4.3 Thermal Wear Protection & Burst-Spurt Scheduling
Continuous max-load execution accelerates physical degradation on consumer-grade laptop and workstation components. The framework enforces hard limits to preserve hardware longevity:
1.  **Intermittent Spurt Execution:** Calculations are dispatched in short, non-continuous spurts rather than prolonged max-wattage calculations. 
2.  **Automated Cooldown Timeout Loop:** Upon completing an allocated mathematical burst-spurt cycle, the node daemon initiates a hard, mandatory 1-hour cooldown timeout loop. During this timeout window, the container drops resource draw to absolute zero, allowing cooling fans to spin down and thermal sensors to settle within factory-stock baseline operating margins.

### 4.4 Geographical Selector Engine & Low-Trust Quarantines
To completely block automated botnets, regional collusion vectors, or sybil network poisoning configurations:
1.  **IP Geolocation Heterogeneity:** The central task distribution engine handles scheduling via an IP-to-location mapping framework. The three consumer nodes selected to process a matching mathematical chunk must be explicitly situated across disparate geographical zones and network subnets.
2.  **Low-Trust Redundancy Scaling:** If a node's public key signature logs a history of transmission error thresholds, it drops to a low-trust quarantine tier. Low-trust processing units require **4 or 5 identical matching datasets** verified across parallel independent high-trust nodes before the core registers the operation as passing consensus.
3.  **Outlier Discard Protocol:** Because matrix data packages are broken into heavy structural fragments, an attacker would require thousands of high-spec machines passing geolocation filters to successfully spoof a chunk payload, allowing outlier matrices to be cleanly detected, discarded, and logged as broken transfers.

### 4.5 Real-Time Availability Signals & Stalled Node Re-Routing
To mitigate pipeline deadlocks from unpredictable user activity or localized hardware events:
1.  **Active Lease Headroom:** When a consumer unit initiates a processing spurt, it locks the chunk by broadcasting an active status lease telemetry signal alongside its local operational loop-time limits to the central scheduler.
2.  **Pre-Purge Non-Viable Evacuation Trigger:** The moment a user launches an application registered within the launcher exception maps (e.g., opening a game in Steam or Prism), the daemon intercepts the execution signal. It instantly fires a rapid **"Node Non-Viable"** drop message to the central gateway right before performing its memory and VRAM purge.
3.  **Immediate Pipeline Re-Routing:** Upon receiving the non-viable alert, the central scheduling grid drops the lease from the stalling machine and instantly re-routes the micro-chunk payload to a fresh set of open nodes, preserving continuous pipeline throughput.

### 4.6 Gateway Rate-Limiting & Growth Anomaly Filters
To shield the central core's verification engines from deliberate distributed denial-of-service (DoS) hash overloading spikes:
1.  **Node Acquisition Analysis:** The edge network gateways analyze incoming node registry graphs against a strict organic growth threshold curve.
2.  **Anomaly Mitigation Triggers:** A rapid, massive influx of unverified node registration attempts disproportionate to typical community metrics throws immediate system-wide warning flags. The gateway layer automatically down-scales ingress permission thresholds, throttles incoming socket rates, and drops suspicious connections into sandboxed, dead-end calculations until their unique hardware footprints and routing paths can be vetted.

---

## 5. Cross-Distro Independent Architecture (`lambda-core`)

To ensure the framework can scale globally without forcing dependencies on commercial gaming platforms, the compute engine is bifurcated into a completely decoupled, platform-agnostic system service.

### 5.1 Standalone System Daemon (`lambdad`)
*   **Headless Background Execution:** The engine can be deployed as a native, lightweight background service (`lambdad`) via standard cross-distribution package managers (`pacman`, `apt`, `dnf`).
*   **Privilege Demotion & Capabilities Lockdown:** To maintain strict host security boundaries, the service file immediately drops root privileges post-initialization, executing under a dedicated non-privileged user space account (`User=lambda`). It retains only highly granular system boundaries via specialized Linux capability assignments (e.g., `CAP_SYS_NICE` for hardware priority thread management).
*   **Namespace Sandboxing:** The daemon is packaged as a standard OCI container image or Flatpak runner, executing inside an isolated, unprivileged namespace with zero physical read or write parameters assigned to the user's home directories.
*   **Anonymity Layer:** No centralized registration or email account creation is required to participate. Nodes authenticate with the central core using exclusively an automatically generated, local cryptographic public key signature.

### 5.2 Cross-Platform Windows Integration Ecosystem
To capture the massive volume of high-specification gaming and workstation hardware currently running on Windows environments, the architecture implements a dual-path Windows integration layer.
*   **Windows 11 Execution Pathway (WSL2 Kernel Integration):** Windows 11 and virtualization-enabled hosts can utilize the native Linux kernel foundation built into Windows Subsystem for Linux (WSL2). The standard Linux container runs within a lightweight utility VM, allowing the engine to direct raw GPU compute power (via nested virtual GPU drivers) straight to the calculations without modifying the host operating system.
*   **Windows 10 Execution Pathway (Native Win32 Binary Fallback):** For Windows 10 systems or environments where virtualization is disabled, a standalone Win32 background service binary handles processing. This service mimics the resource allocation engine, mapping directly to Windows low-priority thread pools to prevent desktop stuttering.

### 5.3 Steam Interoperability Hooks & Privacy-Focused Attestation
While `lambda-core` executes independently at the system level, commercial clients like the Steam launcher can hook into the local daemon's status to provide gamified community milestones.
*   **Unidirectional Local IPC Socket:** The daemon exposes an unprivileged, open local Unix domain socket (`/run/lambda/lambda.sock`) enforcing standard filesystem permissions (`0660`) locked to an authorized user group. Client extensions read this socket unidirectionally to retrieve raw confirmation hashes and milestone states; the engine is hardcoded to never parse inbound execution strings from external client APIs, creating an absolute firewall against open-source licensing cross-contamination.
*   **Non-Quantified Attestation Engine:** To destroy the monetary and structural incentive for automated macro account farming, the framework completely rejects tiered or quantified reward scaling (e.g., running X hours to unlock a rare asset). The integration profile badge behaves as a common, standard attestation of baseline network solidarity.
*   **Economic Constraint Profiling:** If a user flags financial constraints or costly electricity zones via the configuration questionnaire, the scheduler transitions the machine to an alternative low-throughput profile. These users are granted distinct variant badge configurations (e.g., *Wallet-Aware Sentry*) honoring their contribution without burning wall power.
*   **Legacy / Decommissioned Core Status:** Users retain the sovereign right to hide or disable milestone visibility entirely. Additionally, a profile can flag its token status to a permanent *Decommissioned Core* or *Legacy Support* state, enabling historical contribution display without falsifying active processing status if the underlying machine goes offline.

---

## 6. Strategic Institutional Target Framework

For deployment beyond individual hobbyist infrastructure, the open-source architecture targets entities specializing in large-scale network orchestration and digital rights:

1.  **The Linux Foundation:** The primary oversight body for global open-source infrastructure; optimal for establishing the independent compute daemon standard across distributions.
2.  **The Cloud Native Computing Foundation (CNCF):** The governing authority on container orchestration (`containerd`, Kubernetes); ideal for optimizing asynchronous container scheduling across unpredictable, volatile consumer hardware grids.
3.  **Performance Distribution Maintainers (Arch Linux / CachyOS Teams):** Essential for debugging low-level host scheduler hooks, performance optimization, and granular kernel-level undervolting parameters.
4.  **The Electronic Frontier Foundation (EFF):** Relevant for auditing and reinforcing the platform's strict architectural parameters regarding user anonymity, digital sovereignty, and physical data airgaps.