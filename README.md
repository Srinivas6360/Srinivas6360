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
