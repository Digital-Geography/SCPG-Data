# SCPG--Data

## Introduction  
This repository contains data collected through a web-based **geo-questionnaire**, launched as a self-administered online survey. It was developed as part of a research collaboration between the Department of Geography and Regional Research at the University of Vienna and the Institute of Geoinformatics at Óbuda University. The study examines spatial patterns and factors influencing the **spatial crime perception gap (SCPG)** ([project website](http://cpg.amk.uni-obuda.hu/index.php)).  

The datasets available in this repository include sketched polygons representing the perceived safe and unsafe areas in Budapest and Vienna.

## Survey overview  
The survey consisted of two parts:  

1. **Mapping perceptions of safety**  
   - Participants marked areas on a map where they felt safe or unsafe. Participants were free to mark as many areas as they wished but were required to mark at least one area as either safe or unsafe.  
   - Follow-up questions were asked about these locations.  

2. **General and demographic questions**  
   - Respondents provided insights into their perceptions of safety.  
   - Basic demographic details were collected.  

**Target audience & distribution**

- The survey targeted **residents of Budapest and Vienna (18+ years old)**.  
- Available from **November 27, 2023, to February 20, 2024**.  
- Initially distributed via **email (snowball sampling)**.  
- Later shared through:  
  - University websites 
  - Social media (LinkedIn, Facebook, X, WhatsApp)  
  - Student dormitories  
  - Posters in university buildings  
- A reminder was sent three weeks before the closing date.  
- Participants were encouraged to share the survey to expand its reach.

The complete geo-questionnaire is available in the **scpg_geoquestionnaire** file.

## Datasets description
The datasets are provided in **Geopackage** format. 

### **DATA - SKETCHED FEATURES**

These dataset contains the sketched polygons and the responses from the follow-up questionnaire.

**budapest_perceived_safe_areas**  
- *Description:* sketched polygons representing the areas in Budapest that participants perceived as safe.
- *EPSG:* 23700  
- *Rows:* 1,464  

**budapest_perceived_unsafe_areas**  
- *Description:* sketched polygons representing the areas in Budapest that participants perceived as unsafe.  
- *EPSG:* 23700  
- *Rows:* 1,698

**vienna_perceived_safe_areas**  
- *Description:* sketched polygons representing the areas in Vienna that participants perceived as safe.  
- *EPSG:* 31256  
- *Rows:* 255

**vienna_perceived_unsafe_areas**  
- *Description:* sketched polygons representing the areas in Vienna that participants perceived as unsafe.  
- *EPSG:* 31256  
- *Rows:* 297

For attribute details, refer to the **attribute_dictionary_sf** file.  

### **DATA - SCPG (GRID)**

The spatial unit of this dataset is a **hexagonal grid** with an approximate area of **0.15 km²** per cell.  

This dataset includes:  
- **Binomial Test Results**: Applied to the count of overlapping sketched polygons representing perceived safe and unsafe areas within each grid cell. The test determines whether the proportion of observations is statistically significant in classifying the cell as safe or unsafe.  
- **Local Spatial Autocorrelation Analysis (Moran’s I)**: Used to identify crime cold and hot spots by detecting spatial clustering patterns.  

To assess the **spatial crime perception gap**, two datasets were compared:  
1. **Perception Data**: Statistically significant cells classified as perceived safe or unsafe based on binomial test results.  
2. **Reference Data**: Defined by Local Indicators of Spatial Association (LISA) maps, where:  
   - `"High-High"` and `"High-Low"` clusters were considered crime hotspots (unsafe areas).  
   - `"Low-Low"`, `"Low-High"`, and `"not significant"` areas were classified as safe.  

Using map algebra, the perception maps and LISA maps were overlaid and analyzed. Each hexagonal cell was classified into one of the crime perception accuracy categories, allowing an evaluation of how well perceived safety aligns with actual crime hotspots.  

| **Perception \ Reference** | **SAFE** (Reference)                 | **UNSAFE** (Reference)                |
|----------------------------|--------------------------------------|--------------------------------------|
| **SAFE (Perceived)**       | Accurate perception as safe areas (**AS**) | Inaccurate perception as safe areas (**IS**) |
| **UNSAFE (Perceived)**     | Inaccurate perception as unsafe areas (**IU**) | Accurate perception as unsafe areas (**AU**) 

**budapest_crime_perception_gap**  
- *Description:*  this layer contains the perceived safe and unsafe areas, actual crime hotspots and cold spots identified through Moran’s I analysis, and the spatial crime perception gap classification. The gap type is determined by comparing perceived safety with actual crime patterns in Budapest, based on hexagonal grid cells.
- *EPSG:* 23700  
- *Rows:* 3,631

**budapest_perceived_safe_grid**  
- *Description:*  layer showing the count of overlapping sketched polygons representing perceived safe areas in Budapest, aggregated over each hexagonal grid cell. It includes the counts of responses from the follow-up questionnaire.
- *EPSG:* 23700  
- *Rows:* 3,631

**budapest_perceived_unsafe_grid**  
- *Description:* layer showing the count of overlapping sketched polygons representing perceived unsafe areas in Budapest, aggregated over each hexagonal grid cell. It includes the counts of responses from the follow-up questionnaire.
- *EPSG:* 23700  
- *Rows:* 3,631

**vienna_crime_perception_gap**  
- *Description:* this layer contains the perceived safe and unsafe areas, actual crime hotspots and cold spots identified through Moran’s I analysis, and the spatial crime perception gap classification. The gap type is determined by comparing perceived safety with actual crime patterns in Vienna, based on hexagonal grid cells.  
- *EPSG:* 31256   
- *Rows:* 2,906

**vienna_perceived_safe_grid**  
- *Description:* layer showing the count of overlapping sketched polygons representing perceived safe areas in Vienna, aggregated over each hexagonal grid cell. It includes the counts of responses from the follow-up questionnaire.
- *EPSG:* 31256   
- *Rows:* 2,906  

**vienna_perceived_unsafe_grid**  
- *Description:* layer showing the count of overlapping sketched polygons representing perceived unsafe areas in Vienna, aggregated over each hexagonal grid cell. It includes the counts of responses from the follow-up questionnaire.
- *EPSG:* 31256   
- *Rows:* 2,906  

For attribute details, refer to the **attribute_dictionary_grid** file.
