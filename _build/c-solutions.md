---
interact_link: content/c-solutions.ipynb
kernel_name: python3
has_widgets: false
title: 'Cooking Solutions'
prev_page:
  url: /e-safety
  title: 'SAFETY - Is the energy safe?'
next_page:
  url: /c-convenience
  title: 'CONVENCIENCE -  How much time is needed to fetch fuel and prepare the stove?'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Cooking solutions

The majority of surveyed households use LPG (121/137). Other solutions include firewood (13 households) and animal waste (3 households). Several households use more than one kitchen, and more than one fuel.

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import os,sys
here = os.path.abspath('')
sys.path.insert(0, os.path.normpath(os.path.join(here, '../../src')))
import hedera_types as hedera
import odk_interface as odk
import mtf
from pivottablejs import pivot_ui
import matplotlib.pyplot as plt

# change plot layout
plt.rcParams["font.family"] = "Tw Cen MT"
plt.rcParams.update({'font.size': 20})

fondesurco = hedera.mfi(2)
odk_data_dir = '../../_datasets/DataODK/'
odk_survey_folder = ['PEPI_19_03_19/','PEPI_FONDESURCO_19_04_17/']
odk_data_name = [odk_data_dir + odk_survey_folder[0] + 'PEPI_results.csv',
                 odk_data_dir + odk_survey_folder[1] + 
                 'PEPI_FONDESURCO_2_results.csv']
fondesurco.gpsFile = '../../_datasets/Fondesurco/HederaGPS/All.txt'
fondesurco.data_client_file = '../../_datasets/Fondesurco/ClientDatabases/data_with_GPS_3.csv'
data = fondesurco.read_survey(odk_data_name)
fondesurco.HH = odk.households(data)
# get summaries of used sources, fuels, stoces
collection_overview = odk.overview(fondesurco.HH,[fondesurco])

sources_summary = odk.summary(collection_overview,
                                  hedera.keys().powerSources,
                              hedera.names('en').powerSources,
                              hedera.keys().powerSourcesColors)
stoves_summary = odk.summary(collection_overview,hedera.keys().stoves,
                             hedera.names('en').stoves,
                             hedera.keys().stovesColors)
fuels_summary = odk.summary(collection_overview,hedera.keys().fuels,
                              hedera.names('en').fuels,
                              hedera.keys().fuelsColors)

```
</div>

</div>

## Fuels per Office
The vaste majority of the sample is connected to the grid

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python

odk.plot_fuel_summary(collection_overview,'en')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/c-solutions_3_0.png)

</div>
</div>
</div>

## Fuel Expenses

Households spend in average less than 30 Soles per month in electricity.



<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
fondesurco.plot_mean_per_office(fondesurco.HH,'cooking_expenses')
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/c-solutions_5_0.png)

</div>
</div>
</div>

## Expenses vs. Source
Only households using LPG for cooking have regular costs. Solid fuels are mainly collected.

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
colors = []
for k in fuels_summary.used_keys:
    ic = hedera.keys().fuels.index(k)
    colors.append(hedera.keys().fuelsColors[ic])
fondesurco.plot_mean_per_category(fondesurco.HH,'cooking_expenses',
                                  'primary_cooking_fuel',
                                  fuels_summary.used_keys,
                                  fuels_summary.used_names,
                                  colors, figName = None)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/c-solutions_7_0.png)

</div>
</div>
</div>
