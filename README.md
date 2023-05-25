# nt-DLS-HSPY-2023
Accounting for error/excess wt% / at% in data:

When taking EDX data, it became apparent there was an issue with the equipment which cause ~3.5wt% (and ~3.5at%) excess of Aluminium that shouldn't be there, determined using standard materials. In order to quantify EDX so far it has been analysed on an Al-free basis, even when the spectra show that Al is present. I'd like to be able to tell Hyperspy to account for this 3.5% excess when doing the quantification so I can then begin to re-analyse data including the Aluminium. 
The 3.5% cannot be taken off after the quantification of at% and wt% as then the values of at% and wt% for all other elements will be incorrect. 

Another way I've considered approaching this has been to work out the excess intensity/counts of Al, adjust the intensity of Al peaks before quantification, and then use the adjusted/corrected intensities to work out the correct at% and wt% 

#excess intensity 
Al_excess = 300 #counts (eg)
intensity = m.get_lines_intensities (xray_lines= 'Al_Ka')
  Al is 1500
Al_new_intense = Al_Ka - Al_excess 

Then apply/integrate this Al intensity with the intensities of the other elements (which are unchanged) in order to quantify at% and wt%.
