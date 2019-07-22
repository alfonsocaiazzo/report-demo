---
interact_link: content/cooking.ipynb
kernel_name: python3
has_widgets: false
title: 'Access to Modern Cooking Solutions'
prev_page:
  url: /elect
  title: 'Access to electricity'
next_page:
  url: http://hedera.online
  title: 'HEDERA'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Cooking solutions


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
plt.rcParams.update({'font.size': 16})

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

## Cooking fuels

### Primary fuels

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 18})
mfi.cooking_fuels_summary(legend=True)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/cooking_3_0.png)

</div>
</div>
</div>

### Attributed describing access to cooking solutions

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 18})
mfi.tier_barh(hedera.keys().attributes_cooking[0:4],hedera.names('en').c_attributes[0:4],legend=True)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/cooking_5_0.png)

</div>
</div>
</div>

### MTF Index (Cooking solutions)
The MTF Index, for each household, is given by the minimum ranking among all attributes

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 18})
mfi.tier_pie('C_Index')
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/cooking_7_0.png)

</div>
</div>
</div>

### MTF Index vs. Cooking Fuel

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
mfi.stacked_tier_per_category('C_Index',hedera.keys().fuels,
                              'primary_cooking_fuel',
                              hedera.names('en').fuels)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/cooking_9_0.png)

</div>
</div>
</div>
