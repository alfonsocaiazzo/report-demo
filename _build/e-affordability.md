---
interact_link: content/e-affordability.ipynb
kernel_name: python3
has_widgets: false
title: 'ASEQUIBILIDAD ¿Pueden los hogares permitirse la compra de electricidad?'
prev_page:
  url: /e-capacity
  title: 'CAPACIDAD ¿Es la capacidad del suministro de electricidad suficiente para los servicios de energía de los hogares?'
next_page:
  url: /e-legality
  title: 'LEGALIDAD ¿Se presta el servicio de electricidad formalmente o por conexiones informales?'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# ASEQUIBILIDAD ¿Pueden los hogares permitirse la compra de electricidad?

Sólo hay dos posibles catego- rizaciones de niveles. Los hoga- res con un costo de consumo su- perior al 5% de sus ingresos es- tán en el nivel 2, de lo contrario en el nivel 5.

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
fondesurco.tier_plots('E_Affordability')
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
