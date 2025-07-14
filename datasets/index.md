---
layout: default
title: Dataset
permalink: /datasets/
nav_order: 2
---

# StarryData Dataset Documentation

## Overview

The StarryData dataset is a comprehensive database containing experimental data extracted from scientific papers on thermoelectric materials. This dataset consists of three main CSV files containing paper information, material samples, and property measurement data.

### Dataset Statistics
- **Total records**: 370,404
- **Papers**: 46,088
- **Samples**: 121,641
- **Measurement curves**: 202,673


## File Structure

### 1. starrydata_curves.csv (Measurement Data)
**Number of records**: 202,673
**File size**: ~25MB

#### Schema Definition

| Column Name | Data Type | Description | Completeness |
|-------------|-----------|-------------|--------------|
| SID | Integer | Unique paper identifier | 100% |
| DOI | String | Digital Object Identifier | 100% |
| composition | String | Material chemical composition | 99.94% |
| sample_id | Integer | Unique sample identifier | 100% |
| figure_id | Integer | Unique figure identifier | 100% |
| prop_x | String | X-axis property name (e.g., Temperature) | 100% |
| prop_y | String | Y-axis property name (e.g., Seebeck coefficient) | 100% |
| unit_x | String | X-axis unit (e.g., K) | 100% |
| unit_y | String | Y-axis unit (e.g., V*K^(-1)) | 100% |
| x | Array[Float] | X-axis measurement values | 100% |
| y | Array[Float] | Y-axis measurement values | 100% |
| created_at | Timestamp | Record creation timestamp | 100% |
| updated_at | Timestamp | Record update timestamp | 100% |
| project_names | Array[String] | Associated project names | 100% |
| comments | String | Additional comments | 49.05% |


#### Data Example
```csv
SID,DOI,composition,sample_id,figure_id,prop_x,prop_y,unit_x,unit_y,x,y,...
6,"10.1021/am405410e","Pb1.00025Zn0.02Te1.02I0.0005",113,79,"Temperature","Seebeck coefficient","K","V*K^(-1)","[299.8597,324.8683,...]","[-0.0001484452,-0.0001602763,...]",...
```

### 2. starrydata_samples.csv (Sample Information)
**Number of records**: 121,641
**File size**: ~20MB

#### Schema Definition

| Column Name | Data Type | Description | Completeness |
|-------------|-----------|-------------|--------------|
| sample_name | String | Sample name | 100% |
| sample_id | Integer | Unique sample identifier | 100% |
| composition | String | Chemical composition formula | 99.91% |
| composition_details | String | Detailed composition information | 19.45% |
| SID | Integer | Unique paper identifier | 100% |
| DOI | String | Digital Object Identifier | 100% |
| created_at | Timestamp | Record creation timestamp | 100% |
| updated_at | Timestamp | Record update timestamp | 100% |
| sample_info | JSON | Detailed sample information | 97.32% |


#### sample_info Field Structure
```json
{
  "Form": {"category": "Bulk", "comment": ""},
  "FabricationProcess": {"category": "Melting", "comment": "Detailed fabrication process"},
  "DataType": {"category": "Experiment", "comment": ""},
  "ThermalMeasurement": {"category": "LaserFlash+DSC", "comment": ""},
  "ElectricalMeasurement": {"category": "SteadyState+4P", "comment": ""},
  "MaterialFamily": {"category": "PbTe", "comment": ""},
  "RelativeDensity": {"category": ">=90%", "comment": ""},
  "GrainSize": {"category": "", "comment": ""},
  "Purity": {"category": "SinglePhase", "comment": ""}
}
```

### 3. starrydata_papers.csv (Paper Information)
**Number of records**: 46,088
**File size**: ~15MB

#### Schema Definition

| Column Name | Data Type | Description | Completeness |
|-------------|-----------|-------------|--------------|
| SID | Integer | Unique paper identifier | 100% |
| DOI | String | Digital Object Identifier | 100% |
| URL | String | Paper URL | 100% |
| issued | JSON | Publication date information | 100% |
| author | Array[JSON] | Author information | 99.97% |
| title | String | Paper title | 100% |
| container_title | String | Journal name (full) | 100% |
| container_title_short | String | Journal name (abbreviated) | 96.58% |
| volume | String | Volume number | 96.85% |
| issue | String | Issue number | 91.60% |
| page | String | Page numbers | 95.08% |
| ISSN | String | ISSN number | 96.15% |
| publisher | String | Publisher name | 100% |
| project_names | Array[String] | Associated project names | 100% |
| created_at | Timestamp | Record creation timestamp | 100% |

## Supported Properties

The dataset includes various thermoelectric and material properties:

### Common Properties
- Temperature
- Seebeck coefficient
- Electrical resistivity / conductivity
- Thermal conductivity
- Power factor
- ZT (figure of merit)
- Carrier mobility
- Hall coefficient
- Magnetic field / Magnetization
- Battery properties (C rate, Cycle number, Voltage, Discharge/Charge capacity)

## Data Completeness Summary

### Overall Completeness
- **Required fields**: 100% (all primary keys and timestamps)
- **Metadata fields**: >90% (most paper information)
- **Optional fields**: Variable (comments, detailed information)

### File-specific Completeness
1. **starrydata_curves.csv**: Average completeness 92.8%
   - >99.9% excluding comment fields

2. **starrydata_samples.csv**: Average completeness 93.2%
   - >99.0% excluding composition_details

3. **starrydata_papers.csv**: Average completeness 97.5%
   - All important fields have >90% completeness

## Data Quality Features

1. **Data integrity**: Complete referential integrity between files via SID, DOI, and sample_id
2. **Measurement data completeness**: All measurement data (x, y arrays) 100% present
3. **Rich metadata**: Paper information includes detailed bibliographic data
4. **Structured information**: sample_info field records detailed experimental conditions in JSON format


## Download

The complete dataset can be downloaded from the [Starrydata2 Web System](https://www.starrydata2.org).

### Dataset Files
- **starrydata_curves.csv** - Measurement data (202,673 records)
- **starrydata_samples.csv** - Sample information (121,641 records)
- **starrydata_papers.csv** - Paper metadata (46,088 records)

### Additional Resources
- [Starrydata2 Web System](https://www.starrydata2.org) - Access the latest data and tools
- [API Documentation](https://www.starrydata2.org/api) - Programmatic access to the data

---
[← Back to Datasets](/datasets/)
