clc; clear; close all;

% Discrete time axis
n = -10:1:10;

% Signal definitions
s1 = 2 * ones(size(n));                  % Step
s2 = double(n >= 0) - double(n < 0);     % r(n) - r(-n)
s3 = sign(n);                            % Signum

% TDM Multiplexing (interleaving)
mux = zeros(1, 3*length(n));
mux(1:3:end) = s1;
mux(2:3:end) = s2;
mux(3:3:end) = s3;
n_mux = 1:length(mux);

% Demultiplex
s1_rec = mux(1:3:end);
s2_rec = mux(2:3:end);
s3_rec = mux(3:3:end);

% Plotting
figure('Name','TDM-PAM Discrete Time (Color-Coded Mux)','NumberTitle','off');

subplot(3,3,1);
stem(n, s1, 'filled', 'Color', [0 0.6 0]); title('Signal 1: Step'); grid on;

subplot(3,3,2);
stem(n, s2, 'filled', 'Color', [0.5 0 0.5]); title('Signal 2: r(n)-r(-n)'); grid on;

subplot(3,3,3);
stem(n, s3, 'filled', 'Color', [0.9 0.4 0]); title('Signal 3: Signum'); grid on;

% Multiplexed signal with per-point color
subplot(3,3,4:6); hold on;
for i = 1:length(mux)
    if mod(i,3)==1
        stem(n_mux(i), mux(i), 'filled', 'Color', [0 0.6 0]);        % Green - Signal 1
    elseif mod(i,3)==2
        stem(n_mux(i), mux(i), 'filled', 'Color', [0.5 0 0.5]);      % Purple - Signal 2
    else
        stem(n_mux(i), mux(i), 'filled', 'Color', [0.9 0.4 0]);      % Orange - Signal 3
    end
end
title('TDM Multiplexed Signal (Color-coded)');
xlabel('Sample Index'); ylabel('Amplitude'); grid on; hold off;

subplot(3,3,7);
stem(n, s1_rec, 'filled', 'Color', [0 0.6 0]); title('Recovered Signal 1'); grid on;

subplot(3,3,8);
stem(n, s2_rec, 'filled', 'Color', [0.5 0 0.5]); title('Recovered Signal 2'); grid on;

subplot(3,3,9);
stem(n, s3_rec, 'filled', 'Color', [0.9 0.4 0]); title('Recovered Signal 3'); grid on;



%FM modulation
Ac=10; %amplitude of carrier wave
fm=10; %frequency of message signal (Hz)
fc=1000; %carrier frequency (Hz)
F=10000; %sampling frequency (Hz)
kf=800; %frequency sensitivity
mi=kf/fm; % modulation index
T=1/F;
t=0:T:0.1;% time vector
 
%1.Message signal
m=sin(2*pi*fm*t);
figure(1);
subplot(311); % plot at 1st position in a 3-by-1 grid 
plot(t,m); xlabel('t(sec)'); ylabel('m(t)');
title('Message signal Vs Time')
 
%Spectrum of message signal
n=length(m); %length returns period of the message signal
M=fftshift(fft(m,n)); %zero-centered fast fourier transform
f=F*[-n/2:n/2-1]/n; %zero-centered frequency range
figure(2);subplot(311); 
plot(f,abs(M));xlabel('f(Hz)'); ylabel('M(f)');
title('Spectrum of Message signal');
 
%2.Carrier wave
c=Ac*sin(2*pi*fc*t);
figure(1); subplot(312);
plot(t,c); xlabel('t(sec'); ylabel('c(t)');
title('Carrier signal Vs Time');
 
%Spectrum of carrier wave
N=length(c);
C=fftshift(fft(c,N));
f=F*[-N/2:N/2-1]/N;
figure(2); subplot(312);
plot(f,abs(C)); xlabel('f(Hz)'); ylabel('C(f)');
title('Spectrum of Carrier wave');
 
%3.FM modulated signal
x_fm=Ac*sin(2*pi*fc*t-(mi*cos(2*pi*fm*t))); 
figure(1); subplot(313);
plot(t,x_fm); xlabel('t(Sec)'); ylabel('x_f_m(t)');
title('FM modulated signal Vs Time');
 
%Spectrum of fm modulated signal
l=length(x_fm);
X_fm=fftshift(fft(x_fm,l));
f=F*[-l/2:l/2-1]/l;
figure(2); subplot(313);
plot(f,abs(X_fm)); xlabel('f(Hz)'); ylabel('X_f_m(f)');
title('Spectrum of FM modulated signal');
