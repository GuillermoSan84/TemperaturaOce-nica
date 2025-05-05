# TemperaturaOceanica
Procesamiento de Temperatura Oceánica (Copernicus GLOBAL_MULTIYEAR_PHY_001_030)
# Procesamiento de Temperatura Oceánica (Copernicus GLOBAL_MULTIYEAR_PHY_001_030)

## 📋 Métodos
1. **Datos fuente**:  
   - Producto: `GLOBAL_MULTIYEAR_PHY_001_030` (Copernicus Marine).  
   - Variable: `thetao` (Temperatura potencial del agua de mar) diaria para mayo 2016.  
   - Área: -124°E a -80°E, 35°N a 10°S.  

2. **Procesamiento en R**:  
   - Cálculo del **promedio mensual** usando el paquete `terra`.  
   - Exportación a GeoTIFF (`temperatura.tif`).  

Resultados: https://github.com/GuillermoSan84/TemperaturaOce-nica/blob/main/temperatura.JPG?raw=true
Disponibilidad de capas en: http://uninmar.icmyl.unam.mx/geoportal#zoom=5&lat=-11320833.54&lon=2475744.62&layers=BOOT

## 🛠️ Código
```r
library(terra)
datos <- rast("cmems_mod_glo_phy_my_0.083deg_P1D-m_1746464206620.nc", subds = "thetao")
promedio <- mean(datos, na.rm = TRUE)
writeRaster(promedio, "temperatura.tif", filetype = "GTiff")
