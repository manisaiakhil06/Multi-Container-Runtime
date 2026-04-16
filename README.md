# 🚀 Multi-Container Runtime System

---

## 👥 Team Information

* **Neeraj R Gowda**
  SRN: PES1UG24CS295

* **Nallamalli Kanaka Mani Sai Akhil**
  SRN: PES1UG24CS290

---

## ⚙️ Build, Load, and Run Instructions

### 🔹 Build the Project

```bash
make
```

### 🔹 Load Kernel Module

```bash
sudo insmod monitor.ko
```

### 🔹 Start Supervisor

```bash
sudo ./engine supervisor ./rootfs-base
```

### 🔹 Create Container Filesystems

```bash
cp -a rootfs-base rootfs-alpha
cp -a rootfs-base rootfs-beta
```

### 🔹 Start Containers

```bash
sudo ./engine start alpha ./rootfs-alpha /bin/sh
sudo ./engine start beta ./rootfs-beta /bin/sh
```

### 🔹 List Running Containers

```bash
sudo ./engine ps
```

### 🔹 View Logs

```bash
cat logs/alpha.log
```

### 🔹 Stop Containers

```bash
sudo ./engine stop alpha
sudo ./engine stop beta
```

### 🔹 Check Kernel Logs

```bash
sudo dmesg | grep monitor
```

### 🔹 Unload Kernel Module

```bash
sudo rmmod monitor
```

---

## 🎥 Demo Video

➡️ [Watch Demo](https://drive.google.com/file/d/1PeXg8sU5VZm--w18kbqiTbApftiEyVTl/view?usp=drive_link)

---

## 📸 Demo with Screenshots

### 🔹 Multi-container Supervision

### 🔹 Metadata Tracking

### 🔹 Bounded-buffer Logging

### 🔹 CLI and IPC

### 🔹 Soft-limit Warning

### 🔹 Hard-limit Enforcement

### 🔹 Scheduling Experiment

### 🔹 Clean Teardown

---

## 🧠 Engineering Analysis

This project uses **Linux namespaces** and **chroot** to provide lightweight container isolation. Each container runs in an isolated environment while sharing the host kernel.

* A centralized **supervisor** manages container lifecycle and prevents zombie processes
* **IPC** is implemented using pipes and CLI-based communication
* Memory limits are enforced using a **kernel module**:

  * Soft limits trigger warnings
  * Hard limits terminate processes
* Demonstrates Linux scheduling using CPU-bound and I/O-bound workloads

---

## ⚖️ Design Decisions & Trade-offs

* Namespace isolation is simple but less secure than advanced virtualization techniques
* A single supervisor simplifies control but introduces a **single point of failure**
* Pipes are used for IPC due to simplicity but have limitations
* Kernel module monitoring provides precise control but requires **root access**

---

## 📊 Scheduler Experiment Results

* **CPU-bound processes** continuously consume CPU resources
* **I/O-bound processes** yield CPU while waiting

➡️ Demonstrates fairness of the **Completely Fair Scheduler (CFS)** in Linux

---

## ✅ Conclusion

This project demonstrates key Operating System concepts:

* Containerization
* Process management
* Inter-process communication
* Memory monitoring
* CPU scheduling

---
