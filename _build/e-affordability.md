---
interact_link: content/e-affordability.ipynb
kernel_name: python3
has_widgets: false
title: 'Salud y Seguridad'
prev_page:
  url: /e-affordability
  title: 'Calidad'
next_page:
  url: /cooking
  title: 'Cocción'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import os,sys

'''
This is an option to load the libraries directly from the HIT library.
However, the path shall be set correctly.
'''
# add the path to HIT
here = os.path.abspath('')
sys.path.insert(0, os.path.normpath(os.path.join(here, '../../src')))

# import HIT libraries
import hedera_types as hedera
import odk_interface as odk
import tiers as mtf

# create the demo institution
sunrise = hedera.mfi(1)
odk_data_dir = '../../_datasets/DataODK/'

odk_survey_folder = ['PEPI_19_03_19/','PEPI_FONDESURCO_19_04_17/']
odk_data_name = [odk_data_dir + odk_survey_folder[0] + 'PEPI_results.csv',
                 odk_data_dir + odk_survey_folder[1] + 
                 'PEPI_FONDESURCO_2_results.csv']
sunrise.gpsFile = '../../_datasets/Demo/GPS.csv'

# read database
data_demo = sunrise.read_survey(odk_data_name)

# aggregate data
HH = odk.households(data_demo)
collections = odk.collections(HH,[sunrise])
```
</div>

</div>

Affordability

<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
sunrise.tier_plots(HH,'E_Affordability')
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/e-affordability_2_0.png)

</div>
</div>
<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/e-affordability_2_1.png)

</div>
</div>
</div>
