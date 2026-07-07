# Introduction to Python 🐍🌊 - JP Math Review 2026 

Introduction to coding in Python for incoming students — **no experience needed**.

By the end you'll be able to:
- install Python and manage packages with **conda**
- open and run a **Jupyter notebook**
- open a **NetCDF** ocean dataset with **xarray**
- make a **bathymetry map** with **cartopy**

---

## ⚙️ Before class — set up your laptop

Please do this **before** the session (it takes 15–30 min and needs internet), so we
can spend our time coding instead of installing. Stuck? Bring your laptop early (I will be in Clark 271 from 12:30) or email me.

### 1. Download Anaconda ==Install Python

Anaconda bundles Python + the science packages + a friendly GUI. Download the installer
for your operating system and run it with the default options:

👉 **https://www.anaconda.com/download**

> You do **not** need to install Python separately — Anaconda includes it.

Check it worked — open a terminal (**Mac:** Terminal · **Windows:** Anaconda Prompt) and run:

```bash
conda --version
```

You should see something like `conda 24.x.x`. ✅

### 2. Download the course files

Click the green **Code ▸ Download ZIP** button at the top of this page and unzip it,
**or** clone with git:

```bash
git clone <this-repo-url>
```

### 3. Download the bathymetry data (GEBCO)

The map exercise uses a NetCDF file of North Atlantic seafloor depth (~100 MB — too big
to keep in the repo).

👉 **Download `gebco_2026_NorthAtlantic.nc` here:** https://drive.google.com/file/d/1LEz1f54o7puOljmkKtLI7TBfmVU1Sl7R/view?usp=sharing

Put the file in the **same folder** as the notebook.

<details>
<summary>Or get it straight from GEBCO</summary>

You can download your own grid from the official GEBCO tool:
1. Go to **https://download.gebco.net/**
2. Draw/enter the area: latitude **30 to 55 °N**, longitude **-75 to -40 °E**
3. Choose format **NetCDF (2D)** and download.
4. Rename it to `gebco_2026_NorthAtlantic.nc`.
</details>

### 4. Build the environment and test

In the terminal, move into the course folder and run:

```bash
conda env create -f environment.yml
conda activate math-review
jupyter notebook
```

A browser opens — you're ready. Full step-by-step with screenshots-worth of detail is in
**[`00_setup.md`](00_setup.md)**.

---

## 📚 What's in this repo

| File | What it's for |
|------|---------------|
| **[`00_setup.md`](00_setup.md)** | Detailed pre-class install instructions |
| **[`Getting_Started.md`](Getting_Started.md)** | Python & conda basics + simple operations to try |
| **[`bathymetry_cartopy.ipynb`](bathymetry_cartopy.ipynb)** | Main exercise: NetCDF → xarray → cartopy map |
| **[`environment.yml`](environment.yml)** | The conda environment for the class |
| `gebco_2026_NorthAtlantic.nc` | The seafloor data (download separately — see above) |

New to Python entirely? Start with **[`Getting_Started.md`](Getting_Started.md)**.

---

## 🆘 Common hiccups
- **`conda: command not found`** → close & reopen the terminal (Windows: use *Anaconda Prompt*).
- **`ModuleNotFoundError`** → you forgot `conda activate math-review`.
- **Can't find the data file** → make sure `gebco_2026_NorthAtlantic.nc` is in the same folder as the notebook.

