## St. Thomas Flood Risk Analysis
A Quarto Website for Spatial Flood-Risk Modeling & Community Exposure Assessment  
🔗 Live Website: https://yanruupenn.github.io/Yanru-Fang_Final_Project/

### Project Overview
Steep terrain, concentrated coastal development, and limited drainage capacity make St. Thomas, U.S. Virgin Islands highly vulnerable to flooding. Seasonal storms and extreme rainfall rapidly channel runoff from volcanic hillsides into densely populated coastal communities.

This project develops a Python-based ML framework integrating: 
- urban flood inventory construction
- flood susceptibility modeling (Random Forest)
- shelter-accessibility analysis (Pandana)
- community-level flood-risk mapping
- exposure and equity disparities.

**Meets required project criteria:**  
- 3+ independent data sources  
- Complex spatial ops (joins, raster extraction, distance transforms)  
- Street-network analysis (Pandana)  
- Raster processing (rasterio, numpy)  
- Machine learning (susceptibility prediction)  
- Multiple interactive visualizations (Folium, Altair)

### Repository Main Structure
- index.qmd # Project overview
- about.qmd # About me
- stthomas.qmd # Study area introduction
- urban-flood-inventory.qmd # Inventory construction & sampling
- flood-susceptibility.qmd # Random Forest susceptibility model
- shelter-seeking.qmd # Pandana accessibility analysis
- community-flood-risk-map.qmd # Interactive Folium map
- exposure-disparities.qmd # Altair risk-inequity visualization
- vis/ # Exported HTML visualizations
- images/ # Static figures
- styles.css # Custom styling
- quarto.yml # Quarto site configuration

### Key Features
- **Urban Flood Inventory**  
   - 400 flooded & 400 non-flooded samples derived from FEMA/USVI flood zones and DEM-filtered safe areas (>5 m).
   - Overlapping points removed; dataset stored as GeoJSON.
   - Split 70/30 for machine-learning model development.

- **Flood Susceptibility (Random Forest)**  
   - 14 predictors including elevation, slope, ghut distance, tsunami exposure, and 13 land-cover classes.
   - Raster predictors extracted using rasterio.sample; land cover one-hot encoded.
   - Random Forest classifier tuned via cross-validation.
   - Performance: Accuracy = 0.85, AUC = 0.94.
- **Shelter Accessibility (Pandana)**  
   - Pandana used to compute shortest walking distance to nearest shelter.
   - Distances mapped to buildings; accessibility hot/cold spots identified.
   - Several peripheral communities exceed 2,000–3,500 m walking distance.

- **Community Interactive Map (Folium)**  
   - Combines:building-level susceptibility; shelter distance; parcel land value; composite exposure classification
   - Reveals vulnerability clusters along:southern corridor; eastern shoreline; northern hillsides

- **Exposure Disparities (Altair)**  
   - Interactive Altair scatterplot links land value and shelter distance.
   - Low-value parcels (<200 USD/m²) exhibit longer travel distances to shelters.
   - High-susceptibility parcels disproportionately fall into lower-value groups.

### Data Sources
| Dataset              | Source                | Format                  | Description                        |
| -------------------- | --------------------- | ----------------------- | ---------------------------------- |
| Flood Hazard Zones   | USVI Open Data Portal | GeoJSON / SHP           | FEMA-based high-risk flood areas   |
| Tsunami Hazard Zones | USVI Open Data Portal | GeoJSON                 | Coastal inundation risk            |
| Land Cover           | USVI Open Data Portal | Raster TIFF             | 13-category surface classification |
| Ghut Networks        | USVI Open Data Portal | SHP                     | Drainage channels                  |
| Building Footprints  | USVI Government       | GeoJSON                 | Residential structures             |
| Parcel Land Value    | USVI Government       | GeoPackage / SHP        | Land value & ownership             |
| Road Networks        | OpenStreetMap         | OSM XML / Pandana graph | Street network routing             |

| Raster                  | Source    | Format | Description                                |
| ----------------------- | --------- | ------ | ------------------------------------------ |
| DEM (10 m)              | USGS 3DEP | TIFF   | Elevation model                            |
| Slope Raster            | Derived   | TIFF   | DEM gradient representing runoff potential |
| Distance-to-Ghut Raster | Derived   | TIFF   | Euclidean distance to drainage channels    |
- Large raster files (DEM, slope, ghut distance) exceed GitHub 100MB limit and are not included. These files can be downloaded from USGS and NOAA.
### Results Summary
- High/very high risk: southern coast & eastern urban corridor; moderate: inner basins; low: central ridges.  
- Terrain/drainage dominate importance; coastal hazards amplify shoreline risk.  
- Compound risk: steep slopes → lowlands; coastal zones; shelter access >2–3.5 km.  
- Lower-value housing overlaps high susceptibility → double burden (hazard + low evacuation access).

### Build Locally
- Install Quarto: https://quarto.org/docs/get-started/  
- `git clone https://github.com/Yanruupenn/Yanru-Fang_Final_Project.git`  
- `quarto render` (outputs to /docs for GitHub Pages)

### Author
Yanru Fang — Master of City & Regional Planning, UPenn  
Interests: geospatial analytics, urban design, resilience planning  
Portfolio: https://www.linkedin.com/in/yanru-fang-906864324
