<h3 align='center'>Heaven’s Light is Our Guide</h3>
<h1 align='center'>Rajshahi University of Engineering & Technology<h1>

<div align="center">
<img src="./logo.png" alt="Figure-2: Result" width="200">
</div>

<h2><u>Course Code</u>: ECE 4124</h2>
<h2><u>Course Title</u>: Digital Signal Processing Sessional</h2>

<br>
<br>

<div style='display: flex; justify-content: space-between;'>
<div>
<h2><u>Submitted To,</u>
<br>Hafsa Binte Kibria                                             <br>Lecturer, Dept. of ECE, RUET</h2>  
</div>
<div>
<h2><u>Submitted By,</u><br>
S.M. Faizul Islam Fair<br>                                                   
Roll: 1810021                                                            </h2>                                                   
</div>

</div>

<br>
<br>
<br>

| Serial | Experiment Name | Link |
|-----------------|----------------|----------------|
| 01 |  Study of Convolution of Two Signals using MATLAB | <a href='#exp_1'>Experiment_1</a>|
| 02 |  Study of Circular Convolution, Plotting of Figures, Summation, Subtraction and Particular Shapes of Two Signals Using MATLAB | <a href='#exp_2'>Experiment_2</a> |
| 03 |  Study of Auto-correlation & Cross-correlation Using MATLAB | <a href='#exp_3'>Experiment_3</a> |
| 04 |  Study of Time Delay of a Signal Using the Cross-correlation Method  | <a href='#exp_4'>Experiment_4</a> |
| 05 | Study of Causal, Anti-causal, Non-causal Signals, Their Respective Poles & Zeros on the Z-plane | <a href='#exp_5'>Experiment_5</a>|


<br>
<br>
<br>
<br>
<br>

<div id='exp_4'>
<br>
<br>

### **<u>Experiment No:</u> 04**

### **<u>Experiment Date:</u> 15.05.2023**

### **<u>Experiment Name:</u> Study of Time Delay of a Signal Using the Cross-correlation Method** 

<br>


### **<u>Theory:</u>**
                 
<br>                 
    Time delay basically means a delay that separates the occurrence of two events, it is the amount of time a signal takes to propagate itself through a system or under specified processing conditions. There is a huge significance of time delay in signal processing applications. It occurs in the various stages of signal processing such as DSP filters, Multirate filters, signal transformation, etc.

<br><br>
                        

In signal processing, cross-correlation is a measure of similarity of two series as a function of the displacement of one relative to the other. This is also known as a sliding dot product or sliding inner-product. It is commonly used for searching a long signal for a shorter, known feature. It has applications in pattern recognition, single particle analysis, electron tomography, averaging, cryptanalysis, and neurophysiology. The cross-correlation is similar in nature to the convolution of two functions.




<br> <br>



### **<u>Code:</u>**
<br>

```clc
clear all

t=0:0.1:40
x1=(t>=0 & t<=10);
x2=(t>=10 & t<=15);
x3=(t>=15 & t<=25);
x4=(t>=25 & t<=40);
s1 = 1*x1+0*x2-1*x3+0*x4;
subplot(3,1,1);
plot(t,s1);
title('Signal');

d = input('Enter delay value:');

x5=(t>=0+d & t<=10+d);
x6=(t>=10+d & t<=15+d);
x7=(t>=15+d & t<=25+d);
x8=(t>=25+d & t<=40+d);
s2 = 1*x5+0*x6-1*x7+0*x8;
subplot(3,1,2);
plot(t,s2);
title('Delayed Signal');

s3 = xcorr(s1,s2);
subplot(3,1,3);
plot(s3);
title('Cross-correlation');
max_index= max(s3);

fprintf('Delay = %d\n', d);
fprintf('Max Index = %d\n', max(s3));
```


<br><br>



### **<u>Output:</u>** 
<br>

<div align="center">
<img src="./Experiment_4/outputWaveshape_exp-4.png" alt="Figure-1: Cross-correlation of Delayed Signal Graphical Output">
<br>
<h4> Figure-1: Cross-correlation of Delayed Signal Graphical Output </h4> 
</div>


<br><br>

<div align="center">
<img src="./Experiment_4/result_exp-4.png" alt="Figure-2: Result" width="300">
<h4>Figure-2: Result </h4> 

</div>
<br><br>


### **<u>Discussion:</u>** 
<br>
At first, a signal was plotted, after that the delayed signal was plotted with the value of time delay. The cross-correlation built-in function was used to correlate the former and latter signals and it was also visualized. The expected result was obtained from the experiment, the delayed time value and max index were also shown.

<br><br>

### **<u>Conclusion:</u>**
<br> 
The experiment was carried out successfully.

<div>
<br>
<br>
<br>
<br>
<br>



<div id='exp_5'>
<br>
<br>

### **<u>Experiment No:</u> 05**

### **<u>Experiment Date:</u> 22.05.2023**

### **<u>Experiment Name:</u>Study of Causal, Anti-causal, Non-causal Signals, Their Respective Poles & Zeros on the Z-plane** 

<br>


### **<u>Theory:</u>**
                 
<br>                 
   In signal processing and system theory, causal, anti-causal, and non-causal signals describe different relationships between the cause and effect of a signal.

<br>
                        

i). Causal Signals: A causal signal is one in which the output values depend only on past and present input values, but not on future input values. In other words, the output at any given time depends only on the past and present input values up to that time. Causal signals are commonly encountered in many physical systems and real-world phenomena. Examples of causal signals include a temperature sensor reading, stock market data, or an audio recording.

ii) . Anti-causal Signals: An anti-causal signal is the opposite of a causal signal. It means that the output values depend only on future and present input values, but not on past input values. In other words, the output at any given time depends only on the present and future input values. Anti-causal signals are less common in practice and often arise in theoretical scenarios. An example of an anti-causal signal could be a prediction of future stock prices based on present and future information, without considering past data.

iii). Non-causal Signals: Non-causal signals are those where the output values depend on both past and future input values. These signals violate the causality principle and are typically considered hypothetical or theoretical constructs. Non-causal signals cannot be realized in practice, but they can be used as mathematical models or as a tool for analysis. They can help understand the behavior of systems or explore theoretical concepts. An example of a non-causal signal could be a mathematical function that produces an output based on both past and future input values.





<br> <br>



### **<u>Code:</u>**
<br>

i). Causal Signal:

```
x=[3 1 2 4]
b=0;
n=length(x);
y=sym('z');
for i=1:n
 b=b+x(i)*y^(1-i);
end
display(b)
z=[];
p=[0]
zplane(z,p)
```

<br>
<br>

ii). Anti-causal Signal:

```
x=[3 1 2 4]
b=0;
n=length(x);
y=sym('z');
for i=1:n
 b=b+x(i)*y^(i-1);
end
display(b)
z=[];
p=[]
zplane(z,p)
```
<br>
<br>

iii). Non-causal Signal:

```
x=[3 1 2 4]
c=input('Enter the Index: ');
disp(c);
b=0;
n=length(x);
y=sym('z');

for i=0:n-1
    if i>=c-1
    b=b+x(i+1)*y^(c-i-1);

    else
    b=b+x(i+1)/y^(i-c+1);
    end
end    

display(b)

z=[];
p=[0]
zplane(z,p)
```

<br><br>



### **<u>Output:</u>** 
<br>
i). Causal Signal:
<br>
<div align="center">
<img src="./Experiment_5/causal_outputWaveshape_exp-5.png">
<br>
<h4> Figure-1: Poles and Zeros Graphical Output </h4> 
</div>


<br><br>

<div align="center">
<img src="./Experiment_5/causal_result_exp-5.png" alt="Figure-2: Result" width="300">
<h4>Figure-2: Result </h4> 

</div>
<br><br> <br>

ii). Ani-causal Signal:
<br>
<div align="center">
<img src="./Experiment_5/anti-causal_outputWaveshape_exp-5.png">
<br>
<h4> Figure-1: Poles and Zeros Graphical Output </h4> 
</div>


<br><br>

<div align="center">
<img src="./Experiment_5/anti-causal_result_exp-5.png" alt="Figure-2: Result" width="300">
<h4>Figure-2: Result </h4> 

</div>
<br><br><br>

iii). Non-causal Signal:
<br>
<div align="center">
<img src="./Experiment_5/non-causal_outputWaveshape_exp-5.png">
<br>
<h4> Figure-1: Poles and Zeros Graphical Output </h4> 
</div>


<br><br>

<div align="center">
<img src="./Experiment_5/non-causal_result_exp-5.png" alt="Figure-2: Result" width="300">
<h4>Figure-2: Result </h4> 

</div>
<br><br>


### **<u>Discussion:</u>** 
<br>
From this experiment, we’ve learnt about causal, anti-causal and non-causal signals and also observed their respective poles and zeros.
<br>
<br>

A causal signal is a sequence that has values only for nonnegative indices or time instances. When we apply the Z-transform to a causal signal, we typically obtain a rational function with a region of convergence (ROC) that encompasses the unit circle. 
<br>
<br>

Again, an anti-causal signal, on the other hand, is a sequence that has values only for negative indices or time instances. When we apply the Z-transform to an anti-causal signal, we typically obtain a rational function with a region of convergence (ROC) that encompasses the exterior of the unit circle. 
<br>
<br>

Lastly, a non-causal signal is a sequence that has nonzero values for both positive and negative indices or time instances. Although the Z-transform can still be computed for a non-causal signal, the resulting expression may not be a rational function, and the ROC may form a ring or annulus in the Z-plane.


<br><br>

### **<u>Conclusion:</u>**
<br> 
The experiment was carried out successfully.

</div>