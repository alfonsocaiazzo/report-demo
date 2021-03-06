---
interact_link: content/elect.ipynb
kernel_name: python3
has_widgets: false
title: 'Access to electricity'
prev_page:
  url: /gps
  title: 'Map & Overview'
next_page:
  url: /cooking
  title: 'Access to Modern Cooking Solutions'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Electricity sources

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
plt.rcParams["font.family"] = "Arial"
plt.rcParams.update({'font.size': 20})

odk_data_dir = '../../_datasets/DataODK/'
odk_folder_dir = 'HEDERA_SDG7/'
#odk_folder_dir = 'HEDERA_SDG7_19_07_05/'
## @brief name of the file (this should not be changed, it is set from ODK)
odk_data_name = 'HEDERA_SDG7_results.csv'


# initialize the institution
mfi = hedera.mfi(4)
# read database
data = mfi.read_survey(odk_data_dir + odk_folder_dir+odk_data_name,
                           delimiter='-')



mfi.HH = odk.households(data)
```
</div>

</div>

### Attributes describing the access to electricity

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 18})
mfi.tier_barh(hedera.keys().attributes_electricity[0:8],
              hedera.names('en').e_attributes[0:8],legend=True)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/elect_3_0.png)

</div>
</div>
</div>

### MTF Index (Access to electricity)

The MTF Index is given, for each household, by the minimum ranking among all considered attributes.

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 18})
mfi.tier_pie('E_Index')

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/elect_5_0.png)

</div>
</div>
</div>

## Electricity sources
### Primary sources

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
mfi.electricity_sources_summary(legend=True)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/elect_7_0.png)

</div>
</div>
</div>

### Secondary sources

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
mfi.electricity_sources_summary(legend=True,primary=False,secondary=True)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/elect_9_0.png)

</div>
</div>
</div>

### Primary and Secondary

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 18})
collection_overview = odk.overview(mfi.HH,mfi)
odk.plot_electricity_sources(collection_overview,'en')
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/elect_11_0.png)

</div>
</div>
</div>

## MTF Electricity Index vs. Primary Source

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 24})
mfi.stacked_tier_per_category('E_Index',hedera.keys().powerSources,
                              'primary_electricity_source',
                              hedera.names('en').powerSources,legend=True)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/elect_13_0.png)

</div>
</div>
</div>
