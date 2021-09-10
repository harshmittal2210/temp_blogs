# Male Female Voice Recognition

This is a project which I made using MATLAB. As the title suggests it is a simple application which detects the gender of the person.

### Prior Information Utilized:
- The fundamental frequency of a typical male ranges somewhere from 85 Hz to 180 Hz.
- The fundamental frequency of typical female ranges somewhere from 155 Hz to 255 Hz.

Thus we set the threshold frequency to be 160Hz i.e. if the calculated frequency of the audio is more than 160Hz then it is Female voice and if less then it is Male voice.

### Methodology:

<img align="center" src="https://miro.medium.com/max/875/1*MDyY47QowvUYdwe4tGnJvA.jpeg">

In the above workflow, each frame is passed through a low pass filter so that only voice signal remains and rest is discarded. 
This help in increasing accuracy. For each frame mean is subtracted from all the values and then the zero-crossing method is used to find the frequency.
At the end, the mean frequency of all the frames is compared with threshold frequency to identify the gender.

### GUI Application:

<img align="center" src="https://miro.medium.com/max/875/1*tsYOUxJofYAfyYvnUl6cSw.jpeg">


*Source button* — Used to select the source file. By default, it is set to take in only .wav files(can be changed either in the source file)


*Go button* — After the selection from source button to finally select the file name shown in the box, press this button


Another way is directly writing the address of that file and pressing Go button.

In the Message box where in the “Upload New File” is shown provides step by step procedure and errors made by the user while selecting the file and processing it further.

*Generate Graph* — Generates the FFT graph of that audio file.

**Calculate button** — This button calculate the frequency using the algorithm proposed and using the inbuilt algorithm. Also it tells the gender.

> Note- Even though the frequency does not match, the gender predicted is almost same in all the test cases.


### Simulink:


<img align="center" src="https://miro.medium.com/max/875/1*HkZXms9xn9QyLRyWbDj7aQ.jpeg">


Using the From *Multimedia File block* the sample audio is taken as input with 3500 samples per audio channel. 
This is passed to the next block where frequency of each frame is calculated. Following is the code for that function.

```matlab
function y = fcn(x)
Fs=44100;
coder.extrinsic('butter');  % To include butter function in simulink
coder.extrinsic('filter');  % To include filter function in simulink
[b0,a0]=butter(2,325/(Fs/2));
xin = abs(x);
xin=filter(b0,a0,xin);
xin = xin-mean(xin);
x2=zeros(length(xin),1);
x2(1:length(x)-1)=xin(2:length(x));
zc=length(find((xin>0 & x2<0) | (xin<0 & x2>0)));
y = 0.5*Fs*zc/length(x);
```

In the next block *Persistent* is used in order to save the previous result in order to use next time. This is essential for the caculation of mean frequency.

#### Code:

```matlab
function [y,r1] = fcn(u,l)
persistent i
persistent r
if isempty(i)
        i = 0;
end
if isempty(r)
        r = 0;
end
j=l/3500;
i= (u/j)+i;
r=r+1;
r1=r;
y = i;
```

In the final block values are compared with the threshold values.

```matlab
function y = fcn(x,r,l)
y=5;
if r>l/3500
    if x>160
        y=1;
    else
        y=0;
    end
end
end
```

As final result frequency is displayed also

```
0 - Male
1 - Female
```

### Result
-  This technique can identify the correct answer almost in 6 out of 10 test cases.
-  Frequency identified is almost correct but since there is an overlap between the fundamental frequency of male and female, it is not able to accurately identify the gender.

### Future Scope:

Use Machine Learning to classify different voices and then generate more accurate results.

For complete project visit- ![https://github.com/harshmittal2210/Male-Female-Voice-Recognition](https://github.com/harshmittal2210/Male-Female-Voice-Recognition)
