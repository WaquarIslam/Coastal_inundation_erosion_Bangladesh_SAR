
# 🌊 Coastal Inundation and Erosion Mapping Of Bangladesh using SAR
### Satellite-Based Shoreline Change Detection and Flood Exposure Assessment for Climate Adaptation Planning

---

## 🔍 Why This Matters

Coastlines are among the world's most dynamic and risk-exposed environments. In India alone, over **170 million people live within 50 km of the coast**, and studies estimate that **40% of India's coastline is experiencing active erosion**. Under climate change, the compounding of sea-level rise, intensifying cyclones, and increased storm surge frequency is accelerating both inundation risk and shoreline retreat — threatening settlements, fisheries, agriculture, mangrove ecosystems, and critical coastal infrastructure simultaneously.

Effective coastal adaptation — whether through nature-based solutions, managed retreat, or hard engineering — requires accurate, spatially explicit baseline data on **where the coast is changing, how fast, and which assets are exposed**. Traditional survey methods are expensive, slow, and geographically limited. **Satellite remote sensing offers a cost-effective, repeatable, and scalable alternative** capable of detecting shoreline change at centimetre to metre precision over multi-decadal timescales.

This project applies multi-source satellite imagery and SAR analysis to map coastal inundation extents and quantify shoreline erosion and accretion patterns — producing outputs directly applicable to coastal zone management, climate risk disclosure, and adaptation investment prioritisation.

---

## 📌 Key Outputs

| Output | Description |
|---|---|
| **Inundation extent map** | Spatial delineation of flood-affected coastal areas derived from SAR backscatter change |
| **Shoreline change analysis** | Multi-temporal shoreline positions showing erosion, stability, and accretion zones |
| **Erosion rate estimates** | End Point Rate (EPR) and/or Linear Regression Rate (LRR) quantifying shoreline retreat in m/yr |
| **Exposure layer** | Overlay of inundation extent with land use / settlement / infrastructure features |

> **Headline finding:** *[Insert your key result — e.g. "X km of the study coastline showed net erosion averaging Y m/yr over the study period, with Z% of identified erosion zones overlapping with settled or agricultural land."]*

---

## 🛰️ Methodology

### Two Complementary Approaches

This project integrates **passive optical imagery** for shoreline change detection with **Synthetic Aperture Radar (SAR)** for inundation mapping — using each sensor type where it performs best.

```
┌─────────────────────────────────┐    ┌──────────────────────────────────┐
│   OPTICAL (Landsat / Sentinel-2) │    │   SAR (Sentinel-1 C-band GRD)    │
│                                  │    │                                  │
│  Multi-temporal NDWI / MNDWI     │    │  Pre-event vs post-event         │
│  Water-land boundary extraction  │    │  backscatter differencing        │
│  Shoreline position mapping      │    │  Inundation extent delineation   │
│  Erosion / accretion rates       │    │  Works through cloud cover       │
└─────────────────────────────────┘    └──────────────────────────────────┘
                        ↓                              ↓
                Combined coastal hazard exposure layer
                        ↓
          Overlay with settlements, infrastructure, LULC
                        ↓
          Risk-informed adaptation planning inputs
```

### Shoreline Extraction — MNDWI Method

The **Modified Normalised Difference Water Index (MNDWI)** is used to extract the water-land boundary from optical imagery across multiple time periods:

```
MNDWI = (Green − SWIR) / (Green + SWIR)
```

A threshold applied to MNDWI separates water pixels from land, and the resulting boundary is extracted as a vector shoreline. Overlaying shorelines from different dates reveals zones of erosion (landward movement) and accretion (seaward movement).

### Erosion Rate Calculation

Transect-based shoreline change analysis:
- Baseline and monitoring shorelines are intersected with shore-perpendicular transects at regular intervals
- **End Point Rate (EPR):** simple rate of change between two dates
- Change classified as: Severely Eroding / Eroding / Stable / Accreting

### SAR Inundation Mapping

Sentinel-1 SAR (C-band, VV/VH polarisation) pre- and post-event scenes are compared:
- Smooth water surfaces produce strong specular reflection (low SAR backscatter)
- Inundated areas appear as distinct low-backscatter zones against land background
- Change detection isolates newly flooded pixels
- Output: binary inundation mask, suitable for exposure analysis overlay

---

## 📂 Repository Contents

```
coastal-inundation-erosion-rs/
│
├── coastal_inundation_erosion_remote_sensing.pdf   # Full project report — methodology,
│                                                    # maps, and results
└── README.md                                        # This file
```

> **Note:** Analytical code for this project was developed in Google Earth Engine (GEE). A reproducible GEE script will be added in the next release. If you would like the script in the interim, contact via LinkedIn or email.

---

## 🗂️ Data Sources

| Dataset | Platform | Source |
|---|---|---|
| Sentinel-1 SAR GRD (C-band, 10m) | ESA Copernicus | [Copernicus Open Access Hub](https://scihub.copernicus.eu) |
| Sentinel-2 MSI (10m, optical) | ESA Copernicus | [Copernicus Open Access Hub](https://scihub.copernicus.eu) |
| Landsat 8/9 OLI (30m, optical) | NASA/USGS | [EarthExplorer](https://earthexplorer.usgs.gov) |
| SRTM / FABDEM DEM (30m) | NASA / Univ. Bristol | [FABDEM](https://data.bris.ac.uk/data/dataset/s5hqmjcdj8yo2ibzi9b4ew3sn) |
| Coastal LULC | ISRO Bhuvan / GMDA | [Bhuvan Portal](https://bhuvan.nrsc.gov.in) |
| Tidal correction data | NOAA / INCOIS | [INCOIS](https://www.incois.gov.in) |

All primary satellite datasets are **freely and publicly available** through the above portals.

---

## 🌐 Relevance to Coastal Hazard and Climate Adaptation

### For coastal zone management authorities (MoEF, CZMA, state coastal boards):
- Provides objective, satellite-derived evidence for Coastal Regulation Zone (CRZ) enforcement and shoreline demarcation updates
- Identifies priority zones for coastal protection investment (seawalls, mangrove restoration, beach nourishment)
- Quantifies erosion rates needed for Integrated Coastal Zone Management (ICZM) plans

### For climate adaptation planning and finance (World Bank, ADB, GCF, UNDP):
- Baseline shoreline change data is a prerequisite for sea-level rise vulnerability assessments
- Inundation extents feed directly into climate risk screening for coastal infrastructure projects
- Erosion rate data supports cost-benefit analysis of hard vs. nature-based protection options
- Outputs are compatible with the World Bank's CoastSat and SROCC (IPCC Special Report on Ocean) methodologies

### For humanitarian preparedness and early warning (RIMES, NDMA, OCHA):
- SAR-derived inundation maps are operationally deployed during cyclone response (Odisha, Andhra Pradesh, Tamil Nadu coastlines)
- Pre-event shoreline data provides the baseline needed to assess post-cyclone morphological change
- Exposure overlays identify which settlements, roads, and critical infrastructure fall within storm surge reach

### For research and academia (ICZM, blue economy, climate services):
- Multi-temporal shoreline dataset contributes to the national coastal erosion monitoring database
- Methodology transferable to any Indian Ocean or Bay of Bengal coastline
- Connects to upstream flood risk through estuarine backwater and tidal interaction modelling

---

## 🔬 Tools and Technologies

| Tool | Purpose |
|---|---|
| **Google Earth Engine (GEE)** | Cloud-based access to Sentinel-1/2 and Landsat archives; MNDWI computation; SAR change detection |
| **SNAP (ESA)** | Sentinel-1 SAR pre-processing — thermal noise removal, radiometric calibration, terrain correction |
| **ArcGIS / QGIS** | Transect-based shoreline change analysis; cartographic output |
| **DSAS (Digital Shoreline Analysis System)** | USGS tool for transect-based erosion rate computation (EPR, LRR) |
| **Python** | pandas, geopandas, matplotlib — tabular analysis and shoreline statistics |

---

## 📐 Methodological Alignment

This project's approach is consistent with internationally recognised coastal monitoring frameworks:

- **USGS DSAS** — standard tool for quantitative shoreline change analysis worldwide
- **ESA Copernicus Emergency Management Service (CEMS)** — operational SAR inundation mapping protocol
- **IPCC SROCC (2019)** — methodology aligned with sea-level rise exposure assessment guidelines
- **MoEF Coastal Erosion Atlas of India** — national reference for erosion classification and hotspot identification

---

## 🔗 Connection to Climate Change Scenarios

Shoreline erosion observed over historical periods reflects **current baseline dynamics**. Under climate change:

- **Sea-level rise** (projected 0.3–1.0 m by 2100 under SSP5-8.5) will shift the mean shoreline position landward, compounding existing erosion trends
- **Intensifying cyclones** (higher Category 4–5 frequency in the Bay of Bengal) will increase peak storm surge heights, expanding inundation extents beyond historically observed bounds
- **Mangrove loss** (already 40% decline in India since 1980) removes the primary natural buffer against both erosion and surge inundation

The baseline maps produced in this project provide the **reference state** against which future scenario-based projections (using tools such as CoastSat, SFINCS, or Delft3D) can be calibrated.

---

## 👤 Author

**Waquar Ul Islam**  
MS by Research — Disaster Management, IIT Guwahati (CGPA 9.45)  
PG Diploma in Remote Sensing & GIS — IIRS-ISRO  
GATE Geomatics AIR-185  
NASA ARSET: Earth Observations for Humanitarian Applications (2022)

🔗 [LinkedIn](https://linkedin.com/in/waquar-ul-islam) · [GitHub](https://github.com/WaquarIslam)  
📧 waquarulislam@gmail.com

---

## 📎 Related Work — Multi-Hazard Remote Sensing Portfolio

| Repository | Hazard Type | Core Method |
|---|---|---|
| [MS-THESIS](https://github.com/WaquarIslam/MS-THESIS) | Urban Flood | Probabilistic risk, SewerGEMS, CMIP6 climate projections |
| [Cyclone-Shaheen-Oman-2021](https://github.com/WaquarIslam/Cyclone-Shaheen-Oman-2021-ongoing-project-) | Tropical Cyclone | SAR inundation, MERRA-2, IBFWS framework |
| [drought-monitoring-rajasthan-vci](https://github.com/WaquarIslam/drought-monitoring-rajasthan-vci) | Agricultural Drought | MODIS VCI, district-level severity mapping |
| [kolahoi-glacier-snow-cover-mapping](https://github.com/WaquarIslam/kolahoi-glacier-snow-cover-mapping) | Cryosphere / Water Security | Optical RS, snow extent, glacier change |

---

## 🚧 Planned Additions

- [ ] Reproducible GEE script for SAR inundation mapping (Sentinel-1)
- [ ] Reproducible GEE script for MNDWI shoreline extraction and change detection
- [ ] Jupyter notebook for DSAS output analysis and visualisation
- [ ] Future scenario overlay: shoreline position under +0.5m and +1.0m SLR

---

*Methodology aligned with USGS DSAS standards, ESA Copernicus EMS protocols, and MoEF Coastal Erosion Atlas of India classification criteria.*
