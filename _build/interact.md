---
interact_link: content/interact.ipynb
kernel_name: python3
has_widgets: false
title: 'Interactivo'
prev_page:
  url: /gps
  title: 'Geolocalización'
next_page:
  url: /e-access
  title: 'Acceso a Electricidad'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Analísis interactivo
En esa sección es posible calcular y filtrar los datos a nivel de hogar simplemente arrastrando las variables de la lista a la izquierda en la tabla a la derecha

<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import os,sys
here = os.path.abspath('')
sys.path.insert(0, os.path.normpath(os.path.join(here, '../../src')))
import hedera_types as hedera
import odk_interface as odk
import mtf
import pandas as pd
from pivottablejs import pivot_ui

# institution data
sunrise = hedera.mfi(1)
odk_data_dir = '../../_datasets/DataODK/'
odk_survey_folder = ['PEPI_19_03_19/','PEPI_FONDESURCO_19_04_17/']
odk_data_name = [odk_data_dir + odk_survey_folder[0] + 'PEPI_results.csv',
                 odk_data_dir + odk_survey_folder[1] + 
                 'PEPI_FONDESURCO_2_results.csv']
sunrise.gpsFile = '../../_datasets/Demo/GPS.csv'
data_demo = sunrise.read_survey(odk_data_name)
HH = odk.households(data_demo)
collections = odk.overview(HH,[sunrise])

pivot_ui(HH)


```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">

        <iframe
            width="100%"
            height="500"
            src="pivottablejs.html"
            frameborder="0"
            allowfullscreen
        ></iframe>
        
</div>


</div>
</div>
</div>
