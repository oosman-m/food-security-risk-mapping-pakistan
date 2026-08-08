# Spatial Assessment & Food Security Risk Mapping of Pakistan (QGIS):

![Food Security Risk Map](Food_Security_Risk_Map.jpg)

##  Executive Summary:
Food security is a multi-dimensional challenge influenced by climate variability, demographic pressures, and regional agricultural productivity. This project presents a district-level spatial assessment of food security risk across Pakistan using **QGIS**. By combining spatial demographic rasters, climate indicators, and administrative boundary data, a composite risk index was modeled to highlight high-vulnerability regions requiring policy intervention and resource allocation.

---

##  Problem Statement & Practical Impact:
Pakistan faces severe localized food vulnerability due to unpredictable rainfall patterns, unequal crop distribution, and dense population clusters. 

### Key Business & Analytical Insights:
* **Identification of High-Risk Hubs:** Highlights districts in Southern Punjab and parts of Sindh experiencing severe food risk, enabling targeted relief distribution for NGOs, WFP, and government bodies (e.g., NDMA).
* **Precision Resource Allocation:** Helps agricultural policy planners optimize fertilizer, seed, and irrigation subsidies based on spatial climate risk instead of uniform state-wide distribution.
* **Evidence-Based Policy:** Provides visual spatial intelligence for researchers and international development agencies to model agro-climate adaptation strategies.

---

##  Datasets Used:
| Dataset | Type | Source | Purpose / Variable Processed |
| :--- | :--- | :--- | :--- |
| **GADM Boundaries** | Vector (.shp) | [GADM.org](https://gadm.org/) | Administrative Level 2 (Districts) boundary layer |
| **WorldClim Data** | Raster (.tif) | [WorldClim.org](https://www.worldclim.org/) | Historical Mean Precipitation & Temperature layers |
| **Population Density** | Raster / Tabular | PBS / WorldPop | District-level population clustering |
| **Agro-Yield Output** | Tabular (.csv) | Pakistan Bureau of Statistics | Agricultural yield metrics joined to spatial layer |

* **CRS Standard:** `WGS 84 (EPSG:4326)`

---

##  Methodology & Spatial Workflow:

1. **Data Ingestion & Reprojection:**
   * Loaded vector boundaries and multi-source spatial rasters into QGIS.
   * Standardized Coordinate Reference Systems across all layers to `WGS 84`.

2. **Raster Processing & Zonal Statistics:**
   * Executed **Clip Raster by Mask Layer** using GADM District boundaries.
   * Calculated mean climatic and demographic metrics per district polygon using **Zonal Statistics**.

3. **Spatial Data Joining & Field Calculator Indexing:**
   * Joined tabular agricultural yield statistics to vector layer attributes via common District IDs.
   * Computed a weighted composite **Risk Score** in **Field Calculator**:
     $$\text{Risk Score} = w_1(\text{Population Density}) + w_2(\text{Climate Deficit}) - w_3(\text{Crop Output})$$

4. **Graduated Symbology & Cartographic Layout Design:**
   * Applied **Graduated Symbology** using **Natural Breaks (Jenks)** classification into 5 distinct vulnerability tiers.
   * Constructed an executive-ready map layout in **QGIS Print Layout** with standardized elements:
     * Custom dashed Geographic Grid ($3^\circ$ interval) with corner coordinates.
     * Dynamic Legend with plain-language risk tiers (*Very Low* to *Critical Risk*).
     * Double-Box Scale Bar, North Arrow, Data Source Credits, and Cartographer Metadata.

---

##  Technical Challenges Overcome During Development:
* **Spatial Alignment & Frame Boundary Clipping:** Solved canvas misalignment issues during scale modification using the *Move Item Content* tool to keep all administrative boundaries within the print frame.
* **Legend Hygiene & Classification Clean-up:** Removed raw decimal break figures (e.g., *20518–34934*) and replaced them with standard categorical labels (*Very Low*, *Low*, *Medium*, *High*, *Critical Risk*) for clarity.
* **Grid Design Optimization:** Transitioned from heavy, opaque coordinate markers to a subtle, fine dashed gray grid ($3^\circ$ intervals) to retain geographic context without obstructing district boundaries.

---

##  Author & Contact:
* **Mapped By:** Muhammad Usman
* **Affiliation:** Undergraduate Researcher, School of ASAB, National University of Sciences and Technology (NUST), Islamabad
* **Core Skills:** Spatial Data Analytics | QGIS | GIS Mapping | Data Visualization | Agricultural Intelligence

---
*If you find this repository useful for agricultural spatial analytics research, feel free to star ⭐ the repository!*
