# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
close;
wp=input('nter the pass band frequency (Radians)=');
ws=input('Enter the stop band frequency (Radians)=');
alphap=input('Enter the pass band attenuation(dB)=');
alphas=input('Enter the stop band attenuation(dB)=');
T=input('Enter the value of sampling Time=');
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
omegac=omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac=');
disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised=analpf(N,'butt',[0,0],1);
disp(hs_Normalised);
disp('Analog LPF Transfer function H(S)=');
hs=analpf(N,'butt',[0,0],omegac);
disp(hs);
z=poly(0,'z');
Hz=horner(hs,(2/T)*((z-1)/(z+1)))
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);
HW=frmag(Hz,512);
w=0:%pi/511:%pi;
plot(w/%pi,abs(HW));
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response Butterworth IIR LPF');
```

# CALCULATION:

<img width="1089" height="1600" alt="image" src="https://github.com/user-attachments/assets/d07c5c74-4c12-4725-b9dc-fed284ca1dc8" />

<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/30b6ce3b-14c2-46a4-ba0d-0faf5a183057" />



# OUTPUT: 

<img width="1351" height="851" alt="image" src="https://github.com/user-attachments/assets/61158d1f-63dd-4e2f-a782-c3d53ae69b7f" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

