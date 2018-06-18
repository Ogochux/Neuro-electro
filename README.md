# Neuro-electro
First repository 
fs_Hz = 48000; % sampling at 48 kHz
ntrains = 3;  % number of trains
npulses = 20;  % number of pulses per train
pulsefreq_Hz = 100;
iti_s = 1.5;   % inter-interval duration
amp_V = 10;  % Amplitude in volts
pulsedur_s = 100e-6; % pulse duration

dur_s = iti_s * ntrains;
nsamps = ceil(dur_s * fs_Hz);
tt = [1:nsamps] / fs_Hz;  % time series generation
yy = zeros(nsamps, 1);
for tr = 1:ntrains
  t0 = (tr - 1) + iti_s/2;
  for pu = 1:npulses
     t1 = t0 + (pu-1)/pulsefreq_Hz;
     istart = round(t1 * fs_Hz);
     iend = istart + round(pulsedur_s * fs_Hz);
     yy(istart:iend) = amp_V;
  end
end
