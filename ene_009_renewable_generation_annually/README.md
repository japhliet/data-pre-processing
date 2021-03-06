## Annual Renewable Generation Dataset Pre-processing
This file describes the data pre-processing that was done to [the IRENA Renewable Energy Generation dataset](https://irena.org/Statistics/View-Data-by-Topic/Capacity-and-Generation/Statistics-Time-Series) for [display on Resource Watch](https://resourcewatch.org/data/explore/1ed420e2-9283-4ced-b7b6-d5268be7a324).

IRENA annually releases [a publication](https://irena.org/publications/2020/Mar/Renewable-Capacity-Statistics-2020) on capacity and renewable energy generation by nation, year, and technology. This information is readily accessed through their [Data and Statistics page](https://irena.org/Statistics/View-Data-by-Topic/Capacity-and-Generation/Statistics-Time-Series), and can be downloaded from a Tableau dashboard.

#### Data Acquisition
1. Point web browser to:
   [https://public.tableau.com/views/IRENARETimeSeries/Charts?%3Aembed=y&%3AshowVizHome=no&publish=yes&%3Atoolbar=no](https://public.tableau.com/views/IRENARETimeSeries/Charts?%3Aembed=y&%3AshowVizHome=no&publish=yes&%3Atoolbar=no)

2. Ensure right-side dimensions are set to:
   ```
   "level_of_detail": "cumulative",
   "flow": "Electricity Generation",
   "grid_connection": "(all)",
   "region": "(all)",
   "country/area": "(all)",
   "technology": "(all)",
   "sub-technology": "(all)",
   "year": "(all)"
   ```

3. Click the excel icon in the top-right.
   This file can be discarded - it is not needed.
   This step is necessary to activate the button for step 5.

4. Click the download icon in the bottom right, within the Tableau footer

5. Select 'data' from the format options

6. Switch to the 'Full Data' tab

7. Select the 'Show all columns' checkbox

8. Click "Download all rows as a text file"

#### Data Processing
To process this data for display on Resource Watch, the following steps were taken:
1) This processing follows the original choice by IRENA to default to filtering out Pumped Storage hydro plants. These plants are downloaded in the original file to be complete, but are not present in the transformed data.
2) The subset of generation data was taken from the original table.
3) The data was aggregated as a sum based on year, country, sub-technology (e.g. onshore wind, solar thermal, etc), and on-grid/off-grid.

Please see the [Python script](https://github.com/resource-watch/data-pre-processing/blob/master/ene_009_renewable_generation_annually/ene_009_renewable_generation_annually_processing.py) for more details on this processing.

You can view the processed dataset [on Resource Watch](https://resourcewatch.org/data/explore/1ed420e2-9283-4ced-b7b6-d5268be7a324).

#### Data License
The publication [IRENA Renewable Energy Capacity](https://irena.org/publications/2020/Mar/Renewable-Capacity-Statistics-2020) states:

```
Copyright (c) IRENA 2020
Unless otherwise stated, material in this publication may be freely used, shared, copied,
reproduced, printed and/or stored, provided that appropriate acknowledgement is given of
IRENA as the source and copyright holder.
Material in this publication that is attributed to third parties may be subject
to separate terms of use and restrictions, and appropriate permissions from
these third parties may need to be secured before any use of such material.
```

The Tableau download does not clearly denote its license availability.

###### Note: This dataset processing was done by [Logan Byers](https://www.wri.org/profile/logan-byers), and QC'd by [Amelia Snyder](https://www.wri.org/profile/amelia-snyder).