# EXP 2 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 

```c
// Linear Convolution in Scilab

// Input sequences
x = [1 5 10 15];     // Example input signal
h = [1 2 3 4];       // Example impulse response

// Perform linear convolution
y = conv(x, h);

// Display results
disp("Input sequence x(n) = " + string(x));
disp("Impulse response h(n) = " + string(h));
disp("Linear Convolution y(n) = " + string(y));

// --- Plot signals ---
// Plot x(n)
subplot(3,1,1);
n1 = 0:length(x)-1;
plot2d3(n1, x);  
xtitle("Input Sequence x(n)");

// Plot h(n)
subplot(3,1,2);
n2 = 0:length(h)-1;
plot2d3(n2, h);
xtitle("Impulse Response h(n)");

// Plot y(n)
subplot(3,1,3);
n3 = 0:length(y)-1;
plot2d3(n3, y);
xtitle("Linear Convolution y(n)");
```

## PROGRAM (Circular Convolution): 

```c
// Circular Convolution
clc;
clear;

// Input sequences
x = [1 2 3 4];
h = [4 3 2 1];

// Length for circular convolution (take max length)
N = max(length(x), length(h));

// Zero padding if needed
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

disp("Zero-padded input:");
disp(x);
disp("Zero-padded impulse:");
disp(h);

// ---- Circular convolution using modulo ----
y = zeros(1, N);

for n = 1:N
    for k = 1:N
        j = pmodulo(n-k, N) + 1;   // pmodulo avoids negative indices
        y(n) = y(n) + x(k) * h(j);
    end
end

disp("Circular convolution result:");
disp(y);

// ---- Plot results ----
subplot(3,1,1);
plot2d3(0:N-1, x);
title("Input sequence x[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,2);
plot2d3(0:N-1, h);
title("Impulse response h[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,3);
plot2d3(0:N-1, y);
title("Circular Convolution y[n]");
xlabel("n"); ylabel("Amplitude");
```



## OUTPUT (Linear Convolution): 

<img width="768" height="420" alt="2" src="https://github.com/user-attachments/assets/b8b714ba-de39-4f6b-b005-33424568aa41" />


## OUTPUT (Circular Convolution): 

<img width="813" height="409" alt="2c" src="https://github.com/user-attachments/assets/048128c3-2498-4150-80a0-9a81921dfd69" />


## RESULT: 

The linear and circular convolution of the given sequences were successfully verified using SCILAB.
