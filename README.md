# Enterprise Virtualization Sandbox: VirtualBox & Ubuntu Server Deployment

## 📋 Project Overview
This repository documents the end-to-end infrastructure provisioning of a localized, headless virtual lab environment. Utilizing a Type-2 hypervisor, this sandbox establishes a hardened baseline server deployment designed to simulate enterprise networking, logical volume storage structures, and secure administrative boundary conditions.

---

## 🛠 Phase 1: Hypervisor Architecture & Deployment

### 1. Host Preparation & Rationale
* **Platform:** Oracle VM VirtualBox (Type-2 Hypervisor).
* **Objective:** Abstract local physical hardware resources to run isolated guest operating systems securely without modifying the host machine's configuration.
* **Network Isolation Plan:** Establish virtualized network stack environments to facilitate host-to-guest and guest-to-guest data flows while keeping production nodes isolated.

### 2. Implementation Execution
* Executed hypervisor installer scripts on the host platform using optimized base options.
* Instantiated core software-defined network interfaces required for dynamic DHCP bridging and guest communication matrices.

---

## ⚙️ Phase 2: Ubuntu Server Provisioning & Architecture

### 1. Compute & Resource Allocation
To ensure optimal performance and minimal memory footprint, a minimal headless profile was engineered:
* **Guest Operating System:** Ubuntu Server 24.04 LTS (64-bit architecture)
* **Compute Engine:** Allocated **2 Virtual CPUs (vCPUs)** for multi-threaded processes.
* **Volatile Memory:** Provisioned **4096 MB (4GB) RAM** to prevent memory thrashing during system updates.
* **Persistent Storage:** Initialized a **20 GB dynamically allocated** Virtual Hard Disk (VHD).

### 2. Automated Network Stack Configuration
* **Interface Identifier:** Core virtual network interface mapped automatically as `enp0s3`.
* **IP Allocation Infrastructure:** Dynamic host configuration via internal hypervisor DHCP scope.
* **Network Parameters:** IPv4 Address assigned: `10.0.2.15/24`.
* **Outbound Gateway Vector:** Dynamic routing enabled to handle direct translation out to external web servers.
* **Proxy Framework:** Bypassed to maintain a direct external internet handshake.
* **Package Repositories:** Successfully mapped and verified loops against regional distribution archive mirrors.

### 3. Logical Disk Subsystem & File System Layout
Instead of static drive slicing, production-grade logical volume scaling was chosen:
* **Storage Management Layout:** Implemented **LVM (Logical Volume Manager)** architectures.
* **Journaling Structure:** Formatted core storage pools using the high-performance `ext4` filesystem.
* **Mount Topology:** Allocated the full 20 GB block array directly to the system root container (`/`) to allow elastic file system expansions.

### 4. Identity Management & Minimal System Footprint
* **Target Node Hostname:** `ubuntuserver`
* **Default Administrative Account Identity:** `jarvis`
* **Secure Remote Administration:** Provisioned and activated the `OpenSSH Server` daemon during standard bootstrap sequence.
* **Application Footprint Optimization:** Purged/skipped all supplementary application Snaps (Docker, Nextcloud, AWS-CLI) to keep the initial server installation footprint minimal and secure.

### 5. Post-Boot Lifecycle Events & Cryptographic Verification
During the initial initialization phase, system automation logging logs tracked the following:
* **Background Setup Execution:** Monitored real-time background tracking hooks by the `cloud-init` utility.
* **Cryptographic Identity Generation:** Confirmed automated generation of unique target host cryptographic keys (`ECDSA` and `ED25519`) to secure incoming OpenSSH connections.

### 6. System Hardening & Package Modernization
Upon establishing an active shell terminal session under user `jarvis`, automated platform lifecycle maintenance scripts were executed:
* **Package Indexes Synced:** Ran `sudo apt update` to retrieve structural index lists of updated packages.
* **Patch Deployment:** Issued `sudo apt upgrade -y` to deploy the latest kernel security patches, handle software dependencies, and establish system stability.

---

## 💡 Technical Interview Talking Points & Engineering Competencies

* **Headless Linux Administration:** Proves complete capability deploying, navigating, and maintaining enterprise Linux platforms purely via text-based TTY interfaces without a graphical user interface (GUI)—matching modern AWS, Azure, and on-premise production server models.
* **Logical Volume Engineering:** Demonstrates conceptual grasp of Logical Volume Management (LVM) abstractions to reallocate persistent block arrays seamlessly on live infrastructure without data loss.
* **Infrastructure Observability:** Shows ability to interpret text-based low-level log outputs regarding initialization flows (`cloud-init`), hardware network state flags (`enp0s3`), and secure access daemon initialization cycles.

## 🛠 Phase 3: Kali Linux Infrastructure Deployment

### 1. Platform Engineering Approach
* **Deployment Type:** Pre-configured Oracle VirtualBox Virtual Machine Architecture.
* **Target Objective:** Establish an isolated security testing platform inside the virtual subnet.
* **Hardware Allocations Matrix:** 
  * **Compute Allocation:** 2 vCPUs
  * **Volatile Memory:** 2048 MB RAM
  * **Graphics Engine:** VMSVGA with 128 MB Video Memory
* **Status:** Environment imported cleanly via hypervisor engine integration. Default administrative user initialized.

### 2. Post-Deployment Verification
* **Status:** Successful boot to graphical interface (XFCE Desktop Environment).
* **Network Integration:** Interface dynamically verified with full external gateway communication.
* **Administrative Access:** Validated root privilege elevation pathways utilizing the `sudo` command framework.
