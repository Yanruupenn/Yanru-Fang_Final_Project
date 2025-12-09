## St. Thomas Flood Risk Analysis
A Quarto Website for Spatial Flood-Risk Modeling & Community Exposure Assessment  
🔗 Live Website: https://fang

### Project Overview
Steep terrain, concentrated coastal development, and limited drainage capacity make St. Thomas, U.S. Virgin Islands highly vulnerable to flooding. Seasonal storms and extreme rainfall rapidly channel runoff from volcanic hillsides into densely populated coastal communities.

This project develops a Python-based ML framework integrating: urban flood inventory construction; flood susceptibility modeling (Random Forest); shelter-accessibility analysis (Pandana); community-level flood-risk mapping; exposure and equity disparities.

**Meets all required project criteria:**  
- 3+ independent data sources  
- Complex spatial ops (joins, raster extraction, distance transforms)  
- Street-network analysis (Pandana)  
- Raster processing (rasterio, numpy)  
- Machine learning (susceptibility prediction)  
- Multiple interactive visualizations (Folium, Altair)

### Repository Structure
.
├── index.qmd # Project overview
├── about.qmd # About me
├── stthomas.qmd # Study area introduction
├── urban-flood-inventory.qmd # Inventory construction & sampling
├── flood-susceptibility.qmd # Random Forest susceptibility model
├── shelter-seeking.qmd # Pandana accessibility analysis
├── community-flood-risk-map.qmd # Interactive Folium map
├── exposure-disparities.qmd # Altair risk-inequity visualization
├── vis/ # Exported HTML visualizations
├── images/ # Static figures
├── styles.css # Custom styling
└── _quarto.yml # Quarto site configuration

### Key Features
1) **Urban Flood Inventory**  
   400 flooded & 400 non-flooded samples from FEMA/USVI zones + DEM-filtered safe areas (>5 m); overlaps removed; GeoJSON; 70/30 split.

2) **Flood Susceptibility (Random Forest)**  
   14 predictors (elevation, slope, ghut distance, tsunami exposure, 13 land-cover classes); raster extraction + one-hot; tuned RF; Accuracy=0.85, AUC=0.94; 100 m raster (0–1).

3) **Shelter Accessibility (Pandana)**  
   OSM street graph; shortest walking distance to shelter; mapped to buildings; peripheral zones >2,000–3,500 m.

4) **Interactive Map (Folium)**  
   Combines susceptibility, shelter distance, land value, composite exposure; hotspots: south corridor (Charlotte Amalie→Bovoni→Tutu), east shore (Nazareth→Red Hook), north hillsides (Magens Bay, Peterborg).

5) **Exposure Disparities (Altair)**  
   Land value vs shelter distance; high susceptibility in lower-value parcels; EJ signal.

### Data Sources
- Vectors: Flood zones, tsunami zones, land cover, ghuts, buildings, parcel land value (USVI); roads (OSM).  
- Rasters: DEM (USGS 3DEP), slope (derived), distance-to-ghut (derived).
- Large raster files (DEM, slope, ghut distance) exceed GitHub 100MB limit and are not included. These files can be downloaded from USGS and NOAA.

### Results Summary
- High/very high risk: southern coast & eastern urban corridor; moderate: inner basins; low: central ridges.  
- Terrain/drainage dominate importance; coastal hazards amplify shoreline risk.  
- Compound risk: steep slopes → lowlands; coastal zones; shelter access >2–3.5 km.  
- Lower-value housing overlaps high susceptibility → double burden (hazard + low evacuation access).

### Build Locally
- Install Quarto: https://quarto.org/docs/get-started/  
- `git clone https://github.com/your-repo-here.git`  
- `quarto render` (outputs to /docs for GitHub Pages)

### Author
Yanru Fang — Master of City & Regional Planning, UPenn  
Interests: geospatial analytics, ML, urban design, resilience planning  
Portfolio: https://www.linkedin.com/in/yanru-fang-906864324
