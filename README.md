# São Paulo Robbery Geostatistics

Spatial point-pattern analysis of 2016 robbery occurrences in the city of São Paulo, built as a final project for a Geostatistics course. The analysis goes from exploratory maps to point-process statistics (intensity, nearest-neighbor, Ripley's G) and density-based clustering (DBSCAN).

> Built in **Google Colab** as a Jupyter Notebook.

## Data

- **`baseroubos.csv`** — year, month and GPS coordinates (latitude/longitude, WGS84) of each robbery in São Paulo.
- **`Distrito Sao Paulo.zip`** — São Paulo city boundary with its districts (shapefile).

## What the notebook does

1. **Static point map** of 2016 robberies over the São Paulo boundary.
2. **Marked point map** using the **month** as the mark.
3. **Interactive map** (hover a point to see the **year and month** of the robbery).
4. **Intensity estimation** with a **Gaussian kernel** and bandwidth chosen by **Scott's rule** (KDE).
5. **Nearest-neighbor distance histogram**.
6. **Ripley's G function** to assess whether the points are clustered.
7. **DBSCAN clustering** to find robbery clusters, with the configuration **eps = 1200 m** and **min_samples = 50**.

## Tech stack

- **Python** (Jupyter Notebook / Google Colab)
- **GeoPandas** + **Shapely** — geospatial data handling and CRS projection
- **libpysal** — point-pattern statistics (nearest-neighbor, Ripley's G)
- **scikit-learn** — DBSCAN clustering
- **Matplotlib** (+ **Contextily** basemaps) — static visualizations
- **Folium** — interactive map
- **NumPy / Pandas / SciPy** — data processing and kernel density estimation

## How to run

### Google Colab (recommended)
Open the notebook with the **"Open in Colab"** badge at the top of the file, then run the cells in order. Install the extra dependency when prompted:

```python
pip install libpysal
```

Upload `baseroubos.csv` and `Distrito Sao Paulo.zip` (or mount Google Drive) and adjust the file paths in the first cells.

### Local
```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install geopandas shapely libpysal scikit-learn matplotlib contextily folium numpy pandas scipy jupyterlab
jupyter lab                        # open Geoestastica_Atividade_Final_Helber_Soares.ipynb
```

## Notes

- Coordinates are projected to a metric CRS before distance-based steps (nearest-neighbor, DBSCAN) so that `eps` is expressed in meters.
- DBSCAN labels noise points as `-1`; validate clusters visually before interpreting them as hotspots.

## License

MIT
