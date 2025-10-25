# Understanding-the-relation-between-s-and-
clc; clear; close all;

% ----------------------------------------------------------
%   CONSTANTS AND RANGE
% ----------------------------------------------------------
vs = 0.5;                            % Constant extension speed (m/s)
theta = linspace(0.1, pi/2, 300);    % Theta range in radians (0 to pi/2)

% ----------------------------------------------------------
%   EQUATIONS
% ----------------------------------------------------------
s = sqrt(5 - 4*cos(theta));             % Link length (m)
omega = (vs .* s) ./ (2 .* sin(theta)); % Angular velocity (rad/s)
alpha = -cot(theta) .* omega.^2;        % Angular acceleration (rad/s^2)

% ----------------------------------------------------------
%   PLOTTING
% ----------------------------------------------------------
figure('Color', 'w', 'Position', [200 100 800 800]);

% Tick labels in terms of pi for clarity
xticks_vals = [0 pi/12 pi/6 pi/4 pi/3 5*pi/12 pi/2];
xticks_labels = {'0','\pi/12','\pi/6','\pi/4','\pi/3','5\pi/12','\pi/2'};

% --- Plot 1: s vs theta ---
subplot(3,1,1);
plot(theta, s, 'b', 'LineWidth', 2);
grid on;
ylabel('s (m)', 'FontSize', 12);
title('Relationships between s, \omega, and \alpha vs \theta', 'FontSize', 14, 'FontWeight', 'bold');
xlim([0 pi/2]);
xticks(xticks_vals);
xticklabels(xticks_labels);
ylim([min(s)*0.95, max(s)*1.05]);
legend('s(\theta)', 'Location', 'best');

% --- Plot 2: omega vs theta ---
subplot(3,1,2);
plot(theta, omega, 'r', 'LineWidth', 2);
grid on;
ylabel('\omega (rad/s)', 'FontSize', 12);
xlim([0 pi/2]);
xticks(xticks_vals);
xticklabels(xticks_labels);
ylim([0, max(omega)*1.1]);
legend('\omega(\theta)', 'Location', 'best');

% --- Plot 3: alpha vs theta ---
subplot(3,1,3);
plot(theta, alpha, 'g', 'LineWidth', 2);
grid on;
xlabel('\theta (radians)', 'FontSize', 12);
ylabel('\alpha (rad/s^2)', 'FontSize', 12);
xlim([0 pi/2]);
xticks(xticks_vals);
xticklabels(xticks_labels);
ylim([min(alpha)*1.1, max(alpha)*1.1]);
legend('\alpha(\theta)', 'Location', 'best');

sgtitle('Mechanism Kinematics: s, \omega, and \alpha vs \theta (in Radians)', ...
    'FontSize', 16, 'FontWeight', 'bold');
