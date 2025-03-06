# PDVTools 
Simple tools for PDV analysis and velocity extraction - dedicated to one target surface measurement.

# Acknowledgements and references

## Author : Laurent Berthe (CNRS, PIMM)

-Thanks to Gabriel Prudhomme. 

-Étude du nuage de particules éjectées sous choc : apports de la Vélocimétrie Hétérodyne. Mécanique des matériaux [physics.class-ph]. 
Ecole nationale supérieure d'arts et métiers, ENSAM, 2014. 
Français. ⟨NNT : 2014ENAM0044⟩. ⟨tel-01165754⟩

https://pastel.hal.science/tel-01165754

- Thanks to :
M. Betz 09/2015

https://github.com/michael-betz/readTrc

Little helper class to load data from a .trc binary file. This is the file format used by LeCroy oscilloscopes.

https://github.com/michael-betz/readTrc

# Files
Base signal for analysis :Tension(Time) from csv file Time,Tension or file comming from .trc binary file from Lecroy 
ShotTest.zip include one shot extraction and raw datas for your own test

# Design PDV 
Additionnal def allow elementary calculation to design Shift according to velocity aimed.  

# Structure and Files Description
class > PDV(Time,Tension,ChainResponse,PDVShift,PDVFactor,FName,ShotNumber)
    -Raw data : Time Tension
    -Chains response (GHz)
    -PDVShift 
    -PDVFactor (m/s/Hz)
    -FName - File name of raw datas   
    -ShotNumber - Files directory
*************************************************************
Directory Structure : 
Working directory
    -PDVWorking.ipynb (Example of use for ShotTest files
    -PDVExtractSignalAndAnalysis.ipynb (Functions including .trc extraction)
    |
    --ShotNumberDirectory
        -RawDatas (file .trc or/and .csv)
        -Graphs 
        -Report
******************************
# Functions

- def DataLoad(self,LinesSuppressed) load data from .csv file Tension(Time). 
- def ManualBaseLineSupress(self,freq_min,freq_max) - Supress Frequencies (Spectrogramm to Zero) from freq_min,freq_max > self.PDVSpectrogramBaseLine 
- def GraphBaseLine(self) - Graph specrogramm without base line (self.PDVSpectrogramBaseLine ) from ManualBaseLineSupress
- def PDVSelectedSignal(self,freq_min,freq_max,time_min,time_max) - Select Spectrogramm from freq_min to freq_max and from time_min to time_max) 
     >self.PDVSpectrogramSelected, self.Time_stftSelected, self.FePDVSelected
- def GraphPDVSelected(self) - Graph selected spectrogram  - self.PDVSpectrogramSelected, self.Time_stftSelected, self.FePDVSelected       
- def PDVSetFrAcquisition(self) - Extract sample rate in GS/s
- def SetPDVFFT(self) - calculate FFT of raw datas :  Tension and related Time
- def GrahPDVSignal(self) - graph raw datas, FFT raw data, 
- def SetSTFTPDV(self,nperseg) - Calculate STFT from raw data on number of point - nperseg
- def GraphSTFTPDV(self) graph STFT
- def SetVelocity(s%matplotlib inlineelf) - calculate velocity m/s
- def GraphSpectrogram(self) - Graph raw data, STFT and velocity spectrogramms
- def PDVReport(self) - pdf report with all datas and graph for basic analysis, datas, FFFT, Spectrogram, baseline.  
- def ExtractVelocityProfile(self) - Manual extraction of velocity profile  - Mouse left = +1 point  - Mouse right = -1 last point - Mouse middle = save&exit
- def ExtractVelocityProfileGraphSave(self)- Draw and graph manual velocity profile
"""
