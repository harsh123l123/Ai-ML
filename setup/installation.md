# Installation and Environment Setup Guide

Setting up your environment correctly is the first step in your AI & ML journey. This guide details how to install Python, configure virtual environments, and install the libraries required to run all notebooks in this repository.

---

## 🛠️ Step 1: Install Python or Conda

We recommend using **Miniconda** (a minimal installer for Conda) or **Anaconda** because it simplifies package management, especially for scientific computing libraries (NumPy, PyTorch) and different CPU/GPU configurations.

### Option A: Installing Miniconda (Recommended)
1. Download Miniconda for your Operating System: [Miniconda Downloads](https://docs.conda.io/en/latest/miniconda.html).
2. Run the installer and follow the instructions.
3. Verify your installation in a terminal or command prompt:
   ```bash
   conda --version
   ```

### Option B: Installing Python (Standard Pip)
If you prefer not to use Conda, ensure you install Python 3.8 to 3.11:
- [Python Official Downloads](https://www.python.org/downloads/)
- Make sure to check the box **"Add Python to PATH"** during installation on Windows.

---

## 📦 Step 2: Create a Virtual Environment

Virtual environments keep dependencies required by different projects separate. This avoids package conflicts.

### Option A: Using Conda (Recommended)
Open your terminal (or Anaconda Prompt on Windows) and run:
```bash
# Create environment named 'ai-ml' with Python 3.10
conda create -n ai-ml python=3.10 -y

# Activate the environment
conda activate ai-ml
```

### Option B: Using Python Virtualenv
If using standard Python, navigate to the repository directory and run:
```bash
# Create venv folder
python -m venv .venv

# Activate the environment
# On macOS/Linux:
source .venv/bin/activate
# On Windows (Command Prompt):
.venv\Scripts\activate.bat
# On Windows (PowerShell):
.venv\Scripts\Activate.ps1
```

---

## 💾 Step 3: Install Project Dependencies

Make sure your virtual environment is **active** (you should see `(ai-ml)` or `(.venv)` in your command line prompt).

```bash
# Upgrade pip first
python -m pip install --upgrade pip

# Install requirements
pip install -r requirements.txt
```

### Installing PyTorch with GPU Support (Optional)
If you have an NVIDIA GPU and want to run PyTorch with CUDA acceleration:
1. Visit the [PyTorch Get Started](https://pytorch.org/get-started/locally/) page.
2. Select your OS, Package (Pip/Conda), and CUDA Version.
3. Run the generated command in your environment.
For example, for CUDA 11.8:
```bash
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

---

## 💻 Step 4: Add Your Environment to Jupyter

To ensure Jupyter Notebook knows where your custom environment is, we register it as a kernel:

```bash
python -m ipykernel install --user --name=ai-ml --display-name "Python (AI-ML)"
```

---

## 🏃 Step 5: Launch Jupyter Notebook

Navigate to the project root directory and start Jupyter:

```bash
jupyter notebook
```

This will spin up a local server and open your web browser. When opening any `.ipynb` notebook file, make sure to set the kernel to **"Python (AI-ML)"** (top right corner of the Jupyter interface).

---

## ❓ Troubleshooting Common Issues

### 1. `ModuleNotFoundError: No module named '...'`
* **Fix**: Ensure your environment is active, you launched Jupyter from the active environment, and the correct kernel (`Python (AI-ML)`) is selected in Jupyter.

### 2. `Microsoft Visual C++ 14.0 or greater is required` (Windows)
* **Fix**: Some libraries need C++ compilers to build from source. Download and install **Visual Studio Build Tools** and select the "Desktop development with C++" workload: [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/).

### 3. CUDA/GPU is not detected in PyTorch
* **Fix**: Run the following code in Python to check CUDA status:
  ```python
  import torch
  print(torch.cuda.is_available())
  ```
  If this returns `False`, verify that your GPU driver is installed and matches the CUDA Toolkit version you installed PyTorch with.
