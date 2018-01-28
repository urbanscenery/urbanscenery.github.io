---
layout: post
title: 확률과통계 기본정리
categories: [etc]
---

$$
P([x, x+a]) = \int_x^{x+a} f_X(t)dt \approx f_X(x)\times a \delta
$$



### Probability Density Function(PDF)

Random variable X가 $f_X$

### Gaussian Distribution, Normal Distribution

Normal random variable은 PDF에 의해 정의된다. **continuous random variable X**의 PDF가 다음과 같은 식을 따를 때
$$
\begin{align*}
f_X(x) = \frac{1}{\sqrt{2\pi\sigma}}e^-(x-\mu)^2/2\sigma^2
\end{align*}
$$

continuous random variable X를 **Gaussian** 혹은 **Normal** 이라 하고 다음과 같이 표기한다.
$$
\begin{align*}
{X \sim Normal(\mu, \sigma) } \space\space or\space\space{X \sim Gaussian(\mu, \sigma) }
\end{align*}
$$
이때 Normal  random variable의 성질은 다음과 같다. 

1. E[X] = &mu; , var[X] = &sigma;^2 
2. &mu;는 임의의 실수값을 가지며 &sigma;는 임의의 0보다 큰 실수값을 가진다.
3. Normal r.v의 PDF가 갖는 그래프는 다음과 같은 형태를 보이며 &mu;에 대해 대칭이다.
  ![](https://urbanscenery.github.io/assets/0128/0128_normaldistribution.jpg)
4. X ~ Normal(&mu;, &sigma;)일 때 X에 대한 선형함수 Y역시 Normal이다.
   이때 Y = aX + b 라면 E[Y] = a&mu;+b, var[Y]=a^2&sigma;^2 이다.




만약 Z ~ Normal(0,1) 일 때 Z를 **Standard Normal** 이라 한다.

위의 normal random variable 의 4번째 성질에 의해 임의의 X ~ Normal(&mu;, &sigma;)를 정규화 하기 위해서

Z = aX + b ~ Normal(0,1)

a = 1/&sigma; , b = -(&mu;/&sigma;) 로 둔다.

