
<p align="center"> 
  <img src="RockfishHabitatMap.png" alt="Map of rockfish habitat suitability" width="500">
</p>

# Rockfish Habitat Modeling Project
This is a project that was completed during my MEM degree at Duke analyzing suitable blue rockfish habitat in Carmel Bay, California. Data was sourced from ROV and multibeam surveys and downloaded via NOAA's National Centers for Environmental Information website.  

## Question
Which of two proposed marine protected areas (MPAs) in Carmel Bay would protect more blue rockfish habitat? I built a habitat suitability model from survey observations and seafloor data, mapped predicted habitat across the bay, and compared how much of it falls within each proposed MPA.
 
## Data
- **Blue rockfish observations** from ROV transect surveys in Carmel Bay
- **Pseudo-absence points**, randomly distributed across the study area
- **Seafloor rasters (10 m resolution):** bathymetry, benthic habitat type, benthic
  complexity, distance from the shelf break (100 m isobath), and distance from kelp beds
- **Proposed MPA boundaries** (two candidate sites)

## Methods
1. **Sampled environmental conditions** at rockfish observation points and at random
   pseudo-absence points (ArcGIS Pro, Sample tool).
2. **Modeled habitat preferences** with a binomial generalized linear model (GLM) in R,
   using AIC-based model selection to choose predictors. Distance from the shelf break
   was dropped from the final model.
3. **Mapped predicted habitat** by applying the model coefficients to the rasters in
   Raster Calculator, converting log-odds to probabilities, and classifying cells with
   probability > 0.5 as habitat.
4. **Compared the MPAs** by calculating the area and percentage of predicted habitat
   within each one (Zonal Statistics as Table).

   Workflows were documented within ArcGIS Modelbuilder

## Key Findings
-  Deeper depths result in lower rockfish presence, higher benthic complexity results in higher incidences of rockfish, and smaller 
distances from kelp beds show higher rockfish presence because it’s essential to their survival
- **MPA [1]** contains [112,300] m² of predicted habitat ([76]% of its area), compared with
  [4,200] m² ([3]%) in MPA [2].
- **Recommendation:** Potential MPA 1 contains more suitable habitat than potential MPA 2 and, as a result, should be proposed as a new MPA. 
