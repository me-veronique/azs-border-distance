# AZS–Border Distance

**Goal:** for customer behavior analysis, I needed to compute the distance from each fuel station (AZS) to the **nearest international border** using station geo-coordinates.

**What the script does**
1) Loads country border geometries from **GeoJSON/JSON** files.  
2) Builds a unified border line.  
3) For every station, finds the nearest point on that line and computes a **geodesic** distance (km).  
Result is saved to CSV with a new column `DistanceToBoarder` (km).

**Libraries**
- Python, **pandas**, **GeoPandas**, **Shapely**, **PyProj** (optionally **pyogrio** for fast I/O).

---

## How to run (simple)
```bash
pip install -r requirements.txt
python -m src.azs_border_distance \
  --borders-dir "C:/data/GADM_CountryBorders_L0" \
  --azs-file    "C:/data/ouoAzs2.csv" \
  --out         "C:/data/ouoAzs2_with_distance.csv"

