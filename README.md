```markdown
# Foundry Local Node Sizing Calculator for Azure Local

This repository contains an interactive, browser-based sizing calculator designed to plan and provision hardware infrastructure nodes for **Foundry Local** deployments running on **Azure Kubernetes Service (AKS) inside Azure Local**.

## 🚀 Key Sizing Logic Included
* **Static Model Weights Memory:** Calculates base VRAM based on parameter count (Billion parameters) and quantized step precision types (FP16, INT8, INT4).
* **Dynamic KV Cache Memory:** Estimates the context window buffer runtime tracking using optimized continuous batching assumptions (~1MB per 1000 tokens for modern models like Llama 3).
* **CUDA Drivers & Activation Overhead:** Factors in a standard 15% execution headroom padding safety threshold.

## 🛠 Supported GPU Profiles in Azure Local
Azure Local isolates and passes physical graphics hardware directly to AKS worker pods via **Discrete Device Assignment (DDA)**. The following NVIDIA GPUs are validated and supported by this application framework:
* **NVIDIA RTX Pro 6000** (Blackwell Server Edition / Ada Generation - 48GB VRAM)
* **NVIDIA L40 / L40S** (Data Center Compute - 48GB VRAM)
* **NVIDIA L4** (Low Profile Edge Inference - 24GB VRAM)
* **NVIDIA RTX A6000 / A5000** (Legacy Generation Passthrough Tracks)

## 📦 How to Deploy to Azure
Because this tool runs entirely client-side using a clean Tailwind CSS layout stack, it can be hosted natively in Azure with near-zero runtime maintenance costs.

### Option A: Azure Static Web Apps (Recommended)
1. Commit `index.html` directly to the `main` branch of this GitHub repository.
2. Navigate to the **Azure Portal** and search for **Static Web Apps**.
3. Click **Create**, link your GitHub account, and select the `foundrylocalnodesizer` repository.
4. Set the build preset configuration to **Custom** and leave the output app location root path as `/`.
5. Click **Review + Create**. Azure will automatically build a global CDN distribution route pointing to your calculator interface.
```

---

If you'd like to automate this deployment fully, let me know:
* Do you want an **Azure Resource Manager (ARM) / Bicep template** to provision the Azure Static Web App workspace automatically? 
* Do you want a **GitHub Actions YAML pipeline workflow** to push updates on every commit?
