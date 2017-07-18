# rev-survivalAnalysis

```
import pandas as pd
import numpy as np 
df1=pd.read_csv("P:/revise_survival_analysis/patient_ids/rev-survival_alpha_1.0_gamma_0.001_0.08_0.07-3.dat_patient_id.csv",header=None)
df2=pd.read_csv("P:/revise_survival_analysis/casesDemographicsForSurvivalAnalysis1.csv")
df2.columns=['mrd_pt_id','pat_id','indexDate','birth_dts','NMH_MRN','NMFF_MRN','gender_nm','race_nm','ethncty_nm','age_atIndex','death_dts','death_flag']
merge=pd.merge(df1,df2,how='left',left_on='mrd_pt_id', right_on='mrd_pt_id')
merge['death_dts'].fillna('2012-03-21',inplace=True)             
merge['days_diff']=pd.to_datetime(merge['death_dts'])-pd.to_datetime(merge['indexDate'])   
merge['days_diff']=merge['days_diff'].dt.days
df=merge[['group','days_diff','death_flag']]
df.to_csv("P:/revise_survival_analysis/cases_survivalCurveInputFile.csv")
from lifelines import KaplanMeierFitter
kmf = KaplanMeierFitter()
import pandas as pd
import os
os.getcwd()
df=pd.read_csv("P:/revise_survival_analysis/cases_survivalCurveInputFile.csv")
df.head()
T = df["T"]
C = df["E"]
```
