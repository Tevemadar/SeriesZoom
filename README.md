# SeriesZoom

SeriesZoom is a pan-and-zoom type online viewer for viewing a collection of high-resolution images in a web browser. A "filmstrip" is provided for easy navigation in the collection (simple "previous/next" navigation is also available). The images are expected to be in a tiled multi-scale representation ([pyramid](https://en.wikipedia.org/wiki/Pyramid_(image_processing))), SeriesZoom is configured to support the Deep Zoom image format in particular ([DZI](https://en.wikipedia.org/wiki/Deep_Zoom)).  
SeriesZoom needs a list of files it's supposed to show. Current configuration gets that list using the "directory" function of the storage system (SeriesZoom is configured to use "EBRAINS data proxy", offering an OpenStack/Swift-like API, "prefix" and "delimiter" parameters are used when navigating the directory tree). If a storage system does not offer "directory" function, this list can be provided in an actual file. The images themselves can either reside in subdirectories, or in .dzip files. These latter are ZIP files with DZI pyramids inside (Deep Zoom pyramid of an actually high-resolution image can easily consist of several million tiles, that are impractical to handle individually on many storage systems). The underlying ZIP-handler operates without downloading the entire (D)ZIP file, and supports the 64-bit ZIP extension too.

## Examples

### DZI

[Data Proxy](https://data-proxy.ebrains.eu/img-38f117b1-c33b-448f-ab46-4800a66c7d8b) user interface link to a "bucket" with Deep Zoom images inside  
[API list](https://data-proxy.ebrains.eu/api/v1/buckets/img-38f117b1-c33b-448f-ab46-4800a66c7d8b?delimiter=/), the actual small JSON that SeriesZoom requests for  
[One small DZI](https://data-proxy.ebrains.eu/api/v1/buckets/img-38f117b1-c33b-448f-ab46-4800a66c7d8b?prefix=F10_BDA_s001.tif/&limit=10000) file listing of one actual DZI pyramid, JSON file with ~4500 entries  
[SeriesZoom](https://tevemadar.github.io/SeriesZoom/?bucket=https://data-proxy.ebrains.eu/api/v1/buckets/img-38f117b1-c33b-448f-ab46-4800a66c7d8b) link displaying the entire series.

### DZIP

[Data Proxy](https://data-proxy.ebrains.eu/ewb-1c0729c3-aac5-4df1-bde6-f1fc37755cbe?prefix=.nesysWorkflowFiles%2FzippedPyramids%2FF10BDA%2F) user interface link leading to a folder with DZIP files  
[API list](https://data-proxy.ebrains.eu/api/v1/buckets/ewb-1c0729c3-aac5-4df1-bde6-f1fc37755cbe?prefix=.nesysWorkflowFiles/zippedPyramids/F10BDA/), the actual small JSON that SeriesZoom requests for  
[SeriesZoom](https://tevemadar.github.io/SeriesZoom/?dzip=https://data-proxy.ebrains.eu/api/v1/buckets/ewb-1c0729c3-aac5-4df1-bde6-f1fc37755cbe/.nesysWorkflowFiles/zippedPyramids/F10BDA/781_2322_3066__F10_BDA_s001.dzip) link displaying the entire series.
