
MATLAB Implementation Steps 
Step 1: Initialize Environment 
clc; 
clear; 
close all;
 Uttam Naik 
Bits Id-2021wa86965 
Step 2: Define Constants 
% Constants 
C = 3e8;                      
f = 2.4e9;                   
Pt = 1;                       
Gt = 1;                      
Gr = 1;                      
% Speed of light in m/s 
 % Frequency in Hz (2.4 GHz) 
% Transmit power in Watts 
 % Transmitter antenna gain (unitless, linear scale) 
 % Receiver antenna gain (unitless, linear scale) 
d = linspace(1, 1000, 100);   % Distance vector from 1 to 1000 meters (100 points) 
Uttam Naik 
Bits Id-2021wa86965 
Uttam Naik 
Bits Id-2021wa86965 
Step 3: Calculate Free Space Path Loss 
FSPL_dB = 20*log10((4*pi*f*d)/c); % FSPL in dB 
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
             
Step 4: Calculate Received Power 
(a) In Watts:                P_r = P_t * 10.^(-FSPL_dB / 10); % Received power in Watts 
(b) In dBm:                P_r_dBm = 10 * log10(P_r * 1000); % Convert to dBm 
 
 
 
 
 
 
 
 
 
 
Step 5: Plot Power vs Distance 
(a) Semilog Plot (Watts): 
figure; 
semilogy(d, P_r, 'b', 'LineWidth', 2); 
xlabel('Distance (m)'); 
ylabel('Received Power (Watts, log scale)'); 
title('Received Power vs Distance (Log Scale)') 
grid on; 
(b) Linear Plot (dBm): 
figure; 
plot(d, P_r_dBm, 'r', 'LineWidth', 2); 
xlabel('Distance (m)'); 
ylabel('Received Power (dBm)'); 
title('Received Power vs Distance (in dBm)'); 
Uttam Naik 
Bits Id-2021wa86965 
grid on; 
Step 6: Compare Multiple Path Loss Exponents 
alpha_values = [2, 3, 4]; 
colors = ['r', 'g', 'b']; 
figure; 
hold on; 
for i = 1:length(alpha_values) 
alpha = alpha_values(i); 
PL_dB = FSPL_dB + 10 * alpha * log10(d / 1); % General path loss 
P_rx = P_t * 10.^(-PL_dB / 10); 
P_rx_dBm = 10 * log10(P_rx * 1000); 
plot(d, P_rx_dBm, colors(i), 'LineWidth', 2); 
end 
xlabel('Distance (m)'); 
ylabel('Received Power (dBm)'); 
Uttam Naik 
Bits Id-2021wa86965 
title('Received Power vs Distance for Different Path Loss Exponents'); 
legend('α = 2', 'α = 3', 'α = 4'); 
grid on; 
Observation 
Distance (m) α = 2 (Free space) α = 3 (Urban) α = 4 (Obstructed) 
10 ~ -40 dBm ~ -60 dBm ~ -80 dBm 
100 ~ -80 dBm ~ -120 dBm ~ -160 dBm 
1000 ~ -120 dBm ~ -180 dBm ~ -240 dBm 
Post-Lab Tasks 
Q1: Comment on Received Power with Respect to Path Loss 
• Received power decreases as distance increases. 
• The higher the path loss exponent (α), the faster the signal drops. 
• In free space (α = 2), power degrades slower than in obstructed or urban environments  
(α = 3 or 4). 
Q2: Plot Graph Between Received Power (in Watts) and Distance 
Uttam Naik 
Bits Id-2021wa86965 
Already done using: 
(a) Semilog Plot (Watts): 
figure; 
semilogy(d, P_r, 'b', 'LineWidth', 2); 
xlabel('Distance (m)'); 
ylabel('Received Power (Watts, log scale)'); 
title('Received Power vs Distance (Log Scale)') 
grid on; 
Uttam Naik 
Bits Id-2021wa86965 
