# AZS–Border Distance (Python)

Compute the geodesic distance from each fuel station (AZS) to the nearest **international border** and export a CSV for analytics (e.g., near-border share, unique border stations, cross-border patterns).

**Stack:** Python, GeoPandas, Shapely, PyProj, (optional) PyOgrio.  
**Output:** CSV with `azsCode` and `DistanceToBoarder` (km).

---

## ✨ What it does
1. Loads **GADM L0** country polygons (GeoPackage/GeoJSON/Shapefile).
2. Merges per-country geometries, snaps adjacent borders, and builds a robust **international border line**.
3. Reads AZS catalog (CSV/Excel) with coordinates.
4. For each AZS:
   - finds the nearest point on the border line (in EPSG:3035),
   - computes **geodesic distance** on WGS84 (PyProj.Geod),
   - writes `DistanceToBoarder` (km, rounded).

> Keeps the exact column name `DistanceToBoarder` to match existing downstream logic.

---

## 🔧 Installation

### Option A — conda (recommended on Windows)
```bash
conda env create -f environment.yml
conda activate azs-border-distance
