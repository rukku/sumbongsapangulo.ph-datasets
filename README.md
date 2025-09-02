# Philippine Flood Control Projects Dataset

A dataset of flood control infrastructure projects across the Philippines, sourced from the Sumbong sa Pangulo site.

## Dataset Overview

- **Format**: GeoJSON
- **Geometry Type**: Point locations
- **Coverage**: Philippines nationwide
- **Records**: 9,855 flood control projects
- **Source**: https://sumbongsapangulo.ph/

## File Structure

```
├── flood_control_projects.geojson    # Main dataset
└── README.md                        # This file
```

## Data Fields

### Project Information
| Field | Type | Description |
|-------|------|-------------|
| `ProjectDescription` | String | Description of the flood control project |
| `ProjectComponentDescription` | String | Detailed component description |
| `ProjectID` | String | Unique project identifier |
| `ProjectComponentID` | String | Component identifier within project |
| `TypeofWork` | String | Type of construction/engineering work |
| `infra_type` | String | Infrastructure type classification |
| `Program` | String | Government program funding the project |

### Geographic Information
| Field | Type | Description |
|-------|------|-------------|
| `Region` | String | Philippine administrative region |
| `Province` | String | Province name |
| `Municipality` | String | City or municipality |
| `LegislativeDistrict` | String | Congressional district |
| `Longitude` | Double | Geographic longitude coordinate |
| `Latitude` | Double | Geographic latitude coordinate |

### Administrative Details
| Field | Type | Description |
|-------|------|-------------|
| `ImplementingOffice` | String | Government agency implementing the project |
| `DistrictEngineeringOffice` | String | Local engineering office responsible |

### Financial Data
| Field | Type | Description |
|-------|------|-------------|
| `ABC` | Double | Approved Budget for the Contract (numeric) |
| `ABC_String` | String | Approved Budget for the Contract (formatted) |
| `ContractCost` | Double | Actual contract cost (numeric) |
| `ContractCost_String` | String | Contract cost (formatted) |
| `FundingYear` | String | Year funding was allocated |

### Timeline Information
| Field | Type | Description |
|-------|------|-------------|
| `InfraYear` | Integer | Infrastructure year |
| `StartDate` | String | Project start date |
| `CompletionDateOriginal` | Date | Originally planned completion |
| `CompletionDateActual` | String | Actual completion date |
| `CompletionYear` | Integer | Year project was completed |
| `ContractID` | String | Contract identifier |
| `Contractor` | String | Company awarded the contract |

## Data Source

**Original Source**: https://sumbongsapangulo.ph/

## Usage Examples
### Load with Python
```python
import geopandas as gpd

# Load the dataset
df = gpd.read_file('flood_control_projects.geojson')

# Basic statistics
print(f"Total projects: {len(df)}")
print(f"Regions covered: {df['Region'].nunique()}")
print(f"Date range: {df['CompletionYear'].min()} - {df['CompletionYear'].max()}")
```


## Data Quality Notes

- Some records may have missing values in optional fields
- Budget amounts available in both numeric and string formats
- Coordinates are provided in decimal degrees
- Date fields may be in various formats (some as strings, others as proper dates)
