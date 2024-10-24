***Guide to old field trip data for CHM410 PFAS analysis***

General points:
- There are cases where one or more calibration curves have clear outliers. Check the goodness-of-fit of your calibration curves before using them! Don't be afraid to filter out points that are clearly erroneous
- Some calibration curves are quite poor quality, leading to high LOD/LOQs. You can skip the LOD/LOQ filtering step and simply flag these values if this is the case, but you still believe that the peaks in the samples are real and quantifiable. 
- Some datasets have multiple calibration datasets for each compound. You cannot use these calibration curves together, you must generate separate calibration curves for each dataset. Use the group_by function and find another column that describes the differences between the calibration curves (Location, a date contained in the sample name, etc) to separate out the different calibration datasets. You will also need to add an extra call to `separate()` to get Sample.name to separate into a numeric concentration. 
- Some older datasets have some missing data for some compounds, which will result in NA values for some compounds on certain samples. Filter these datapoints out when plotting to avoid unexpected issues
- Some biota datasets have multiple dilutions (i.e. 2x and 20x for the same sample). This information is contained within the Sample_name column and should be used to correctly normalize the concentration of each analyte. 
- The biota datasets have separate blanks for the mortar and pestle, blender, and homogenizer. Be careful when subtracting out blanks to make sure that there is an appropriate blank for every sample or you will get NA values. In a pinch, you can use a different blank for a sample (i.e. use the blender blank for a sample prepared using the homogenizer if there is no available homogenizer blank). 

Specific points:
2023 - LOD and LOQs on PFHxA, PFOA, PFHxS, and PFOS are relatively high, likely due to blank contamination. 

2022 - Missing 20MC biota and sediment (example dataset uses 2021 data)

2021 - Two calibration curves, one on 101921, one on 102521. Has a "Date" column to distinguish. PFHxS calibration curve on 101921 is bad - check for outliers. Otherwise, this is probably the best recent dataset. 

2019 - Two calibration curves, one for NIA, one for 20MC. Use "Location" column to distinguish. PFHxS calibration curve for NIA has an outlier. 

2018 - Has two calibration curves for each compound, but they do not apply to specific samples. Labeled as "A" and "B" in the Sample group column. Take the average or use all or some of the data. Remove calibration curve from DataAll or add information to Sample.name to allow it to export.  

2017 - Has two calibration curves for each compound, but they do not apply to specific samples. Labeled "A" to "D" in the Sample group column. Take the average or use all pr some of the data. Remove calibration curve from DataAll or add information to Sample.name to allow it to export. Original data had more analytes. PFOA calibration curve and LOD/LOQ are not ideal. 

2016 - Two calibraition curves for each compound, but they do not apply to specific samples. Labeled as "A" and "B" in the Sample group column. Take the average or use all or some of the data. Remove calibration curve from DataAll or add information to Sample.name to allow it to export. Calibration curve is smaller than in subsequent years, so use a higher cutoff for LOD/LOQ calculation. Original data had more analytes. No biota preparation-specific blanks, all are labeled as 'field'. 
