# Description

Collection of all the csv files for the SEP project.

For the radiation, they use an Arineta CT Scanner, most likely SpotLightTM or SpotLight Duo. Looking at some research documents, they say that the radiation dose present in the equipment of these is lower by a 70% than the average. The problem is that this study was made in 2015, which is 10 years behind the average data from the radiology safety info last updated in 2025. 

Research paper:
https://www.jacc.org/doi/10.1016/j.jcmg.2015.03.005

Radiology info:
https://www.radiologyinfo.org/en/info/safety-xray

Other papers used:
https://www.arineta.com/wp-content/uploads/2024/08/SpotLightTM-and-SpotLightTM-Duo-Product-datasheetMKT-19523EN_Rev-1.30.pdf
https://www.arineta.com/wp-content/uploads/2024/09/MAN-19520EN-DICOM-Conformance-Statement-DireCT.pdf

Papers that I read, but are not verifiable, hence NOT good sources.
https://myheartvision.com/arineta-spotlight-duo-imaging/
https://24x7mag.com/medical-equipment/imaging-equipment/ct/ct-technology-cuts-radiation-levels-cardiac-care/

Hence we are going to assume that the CT Arineta work like average scanners.

Now the way that the average dose of radiation present in a CT scan is calculated is:

The scanner automatically calculates the:
DLP, the CTDIvol multiplied by the length of body scanned:

DLP (mGy·cm) = CTDIvol (mGy) × scan length (cm)

Afterwards depending on the body region taht was scanned the average amount of mSv per DLP differs.

The overall body size also plays a part in this as it influences the ctdi_vol_mGy. 

The 2 parts that will have the data for the radiation are:
patient_region_scan_status.csv; which has most of the important data needed to perform the calculations
patient_total_radiation.csv; which calcaultes the total radiation obtained after each region
region_dlp_references.csv has the reference data that does not change such as the k_factor, scan_length and the average DLP before weight influence, for each region.

I think this is enough to visualize it. This is imo the main way we need to look at radiation. This is temporary dummy data as it has been mostly done by explaining how the database should look (it's keys, level of organizatio, what we learned in datamodeling and databases) along with the calculations that need to be taken into account. This will have to be changed when the data for the radiation will work more like a database which I believe it is needed as radiation burden does seem pretty important for them.