# Getting Started with Python & Conda

Everything you need to set up your laptop **and** your first lines of Python.
No experience needed. 🐍 Please work through the *Setup* part **before class**.

---

# Part A — Setup (do this before class)

The install takes 15–30 min and needs internet. If you get stuck, bring your laptop
early or email me — a broken install is normal and quick to fix in person.

## 1. Install Python with conda

**conda** installs Python *and* the science packages for you, and keeps each project's
packages tidy in a separate "environment."

| Option | Best for | Link |
|--------|----------|------|
| **Anaconda** | beginners — includes a GUI | https://www.anaconda.com/download |
| **Miniconda** | smaller, command-line only | https://docs.conda.io/en/latest/miniconda.html |

> Anaconda **includes Python** — you don't install Python separately.

Check it worked — open a terminal (**Mac:** Terminal · **Windows:** Anaconda Prompt):

```bash
conda --version
```

You should see something like `conda 24.x.x`. ✅

## 2. Get the course files

Click the green **Code ▸ Download ZIP** on the repo page and unzip, **or** with git:

```bash
git clone <this-repo-url>
```

## 3. Download the bathymetry data (GEBCO)

The map exercise uses a ~100 MB NetCDF file — download it and put it in the **same folder**
as the notebooks:

👉 `gebco_2026_NorthAtlantic.nc` — `<GOOGLE DRIVE LINK>`

## 4. Create the environment

From the course folder, build the environment from the file and activate it:

```bash
conda env create -f math-review-env.yaml
conda activate math-review
```

Your prompt changes from `(base)` to `(math-review)`. Do `conda activate math-review`
**every time** you work on this class. To leave: `conda deactivate`.

> No env file? Build one by hand:
> `conda create -n math-review python=3.12 numpy matplotlib xarray jupyter cartopy cmocean`

## 5. Launch Jupyter and test

```bash
jupyter notebook
```

A browser tab opens. Click **New ▸ Python 3** to make a notebook, type this in a cell,
and press **Shift + Enter** to run it:

```python
import numpy as np
import matplotlib.pyplot as plt
import xarray as xr
import cartopy.crs as ccrs
import cmocean
print("All good ✅")
```

If it prints `All good ✅` with no red errors, you're ready. 🎉

---

# Part B — Python basics

Type these into notebook cells and run them one at a time. (There's a ready-made
notebook for this too: **`Simple_Python.ipynb`**.)

## Import packages

A **package** is a toolbox of ready-made code. Import what you need at the top:

```python
import numpy as np              # numbers & arrays
import matplotlib.pyplot as plt # plotting
```

`as np` gives it a short nickname. A `ModuleNotFoundError` usually means you forgot
`conda activate math-review`.

## Variables and types
```python
name = "Woods Hole"   # text (string)
depth = 45            # whole number (int)
temp = 12.5           # decimal (float)

print(name, depth, temp)
print(type(depth))    # <class 'int'>
```

## Math
```python
2 + 3        # 5
10 / 4       # 2.5
2 ** 3       # 8  (2 to the power 3)
17 % 5       # 2  (remainder)
```

## Lists
```python
depths = [10, 25, 40, 55]
print(depths[0])       # first item -> 10
print(depths[-1])      # last item  -> 55
print(len(depths))     # how many   -> 4
depths.append(70)      # add one to the end
```

## A loop
```python
for d in depths:
    print("depth:", d, "m")
```

## A condition
```python
d = 55
if d > 50:
    print("deep")
else:
    print("shallow")
```

## A function
```python
def to_fahrenheit(celsius):
    return celsius * 9/5 + 32

print(to_fahrenheit(12.5))   # 54.5
```

## NumPy arrays
```python
a = np.array([10, 25, 40, 55])
print(a.mean())   # average -> 32.5
print(a.max())    # largest -> 55
print(a * 2)      # multiplies every value -> [ 20  50  80 110]
```

## A quick plot
```python
x = np.array([0, 1, 2, 3, 4])
y = x ** 2

plt.plot(x, y, marker="o")
plt.xlabel("x")
plt.ylabel("y = x²")
plt.title("My first plot")
plt.show()
```

---

## Cheat sheet

| Task | Command |
|------|---------|
| Check conda | `conda --version` |
| Create env from file | `conda env create -f math-review-env.yaml` |
| Create env manually | `conda create -n math-review python=3.12 numpy matplotlib jupyter cartopy cmocean` |
| Activate env | `conda activate math-review` |
| List envs | `conda env list` |
| Start notebook | `jupyter notebook` |
| Run a cell | `Shift + Enter` |

## Common hiccups
- **`conda: command not found`** → close & reopen the terminal (Windows: use *Anaconda Prompt*).
- **`ModuleNotFoundError`** → you forgot `conda activate math-review`.
- **Notebook won't start** → make sure `jupyter` is installed in the active environment.
- **Can't find the data file** → put `gebco_2026_NorthAtlantic.nc` in the same folder as the notebook.
