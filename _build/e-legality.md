---
interact_link: content/e-legality.ipynb
kernel_name: python3
has_widgets: false
title: 'LEGALIDAD ¿Se presta el servicio de electricidad formalmente o por conexiones informales?'
prev_page:
  url: /e-affordability
  title: 'ASEQUIBILIDAD ¿Pueden los hogares permitirse la compra de electricidad?'
next_page:
  url: /e-reliability
  title: 'CONFIABILIDAD ¿Es el servicio de electricidad confiable?'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# LEGALIDAD ¿Se presta el servicio de electricidad formalmente o por conexiones informales?

Sólo hay dos posibles categorizaciones de niveles. Los hogares conectados informalmente están en el nivel 3, de lo contrario en el nivel 5.

### Clasificación MTF

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
fondesurco.tier_plots('E_Legality')
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/e-legality_2_0.png)

</div>
</div>
<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/e-legality_2_1.png)

</div>
</div>
</div>
