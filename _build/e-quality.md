---
interact_link: content/e-quality.ipynb
kernel_name: python3
has_widgets: false
title: 'CALIDAD ¿La fluctuación del voltaje avería los electrodomésticos?'
prev_page:
  url: /e-duration
  title: 'DISPONIBILIDAD ¿Está disponible la fuente de energía cuando la necesita el hogar?'
next_page:
  url: /e-safety
  title: 'SEGURIDAD ¿Es seguro usar el servicio de electricidad o está el hogar arriesgando su salud?'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# CALIDAD ¿La fluctuación del voltaje avería los electrodomésticos?

TEXTO

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
fondesurco.tier_plots('E_Quality')
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/e-quality_2_0.png)

</div>
</div>
<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](images/e-quality_2_1.png)

</div>
</div>
</div>
