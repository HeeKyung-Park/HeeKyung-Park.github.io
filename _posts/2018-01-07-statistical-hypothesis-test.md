---
layout: post
title: Statistical hypothesis test(통계적 가설·검정)
categories : [Statistics]
comments: true
tags : 
- Basic Statistics
---

<div class="message">
  데이터 분석에 근간이 되는 통계적 가설·검정과 용어에 대해 알아보자.
</div>

## <span style='color:#6a9fb5'> 독립변수 & 종속변수</span>
- **독립변수(Independent variable)** <br/>
   = 설명변수(Explanatory variable), 예측변수(Predictor variable), 위험인자(Risk factor) <br/>
   \: 연구자가 의도적으로 변화시키는 변수로, 입렵값이나 원인을 나타낸다. <br/>

- **종속변수(Dependent variable)** <br/>
   = 반응변수(Response variable), 결과변수(Outcome variable), 표적변수(Target variable) <br/>
   \: 독립변수의 변화에 따라 어떻게 변하는지 알고 싶어하는 변수로, 결과나 효과를 나타낸다. <br/>


<br/>

## <span style='color:#6a9fb5'> 귀무가설 & 대립가설</span> 
- **귀무가설(Null hypothesis, $H_0$)** <br/>
   \: 증명하고자 하는 실험과 반대되는 입장, 증명되기 전까지는 효과도 없고 차이도 없다는 영가설

- **대립가설(Alternative hypothesis, $H_{1}$)** <br/>
   \: 귀무가설의 반대로, 연구자가 실험을 통해 규명하고자 하는 가설

   Ex) <br/>
         \- $H_0$ : 새로운 신약은 알레르기에 효과가 없다. <br/>
         \- $H_1$ : 새로운 신약은 알레르기에 효과가 있다. <br/>


## <span style='color:#6a9fb5'> 모집단 & 표본집단 / 모수 & 통계량 </span>
- **모집단(Population)** <br/>
  \: 어떤 정보를 얻고자 하는 전체 대상 또는 전체 집합

- **표본집단(Sample)** <br/>
  \: 모집단으로 부터 추출된 모집단의 부분 집합

 <p align="center"><img width="450" height="auto" src="https://i.imgur.com/GqSXn5B.png"></p>

- **모수(Parameter)** <br/>
  \: 모집단의 특성을 수치로 나타낸 값 (ex. 평균 $\mu$, 분산 $\sigma^2$)

- **통계량(Statistic)** <br/>
  \: 표본의 특성을 수치로 나타낸 값 (ex. 표본 평균 $\hat{\mu} = \bar{X}$, 표본 분산 $\hat{\sigma^2} = s^2$) <br/>
    <span style='color:gray'> ※ hat 기호는 추정량을 뜻한다.</span> 

> 일반적으로, 전수조사가 아닌 이상 모집단에서 모수를 구하기가 어렵다. 결국, 데이터 분석의 목적은 표본집단에서 통계량을 구해 모집단의 모수를 추론하는 것이다.


## <span style='color:#6a9fb5'> 가설·검정</span>
<div class="message">
  <strong>Q1. A학교 1학년 평균키는 162.3cm이다. 전국 1학년 평균키는 162.0cm로 알려져 있을때, <br/>
                    A학교 1학년의 평균키는 160.0cm보다 크다고 할 수 있는가?</strong> <br/>
  <strong>A1.</strong> 0.3cm의 차이면 크다고 할 수 있지 아닐까?, 0.3cm 정도는 크다고 하기엔 부족하지 아닐까? <br/>
  <br/>

  <strong>Q2. "0.3cm의 차이는 유의하다." 주장을 신뢰하기 위해서는 어떠한 조건이 있으면 좋을까?</strong> <br/>
  <strong>A2.</strong> 10명의 평균키보다는 10000명의 평균키는 어떨까?, 사람의 키가 아닌 콩의 크기에서 0.3cm는 유의할 것 같은데??<br/>
</div> 

  \: 문제를 인식하여 가설(hypothesis)를 세우고, 이를 확인하는 과정을 검정(test)라고 한다. 가설·검정을 할 때, 위의 상황처럼 고려할 사항들이 몇가지 있다. 

<strong> 가설(hypothesis) </strong>
- $H_0$ : A학교 1학년의 평균키는 162.0cm 이다. ($\mu_1 = 162.0$)
- $H_1$ : A학교 1학년의 평균키는 162.0cm 보다 크다. ($\mu_1 > 162.0$)

<br/>

<strong> 검정(test) </strong>

<p align="center"><img width="450" height="auto" src="https://i.imgur.com/ez4LhiH.png"></p>

- **기각역(rejection region, $\alpha$)** <br/>
  \: 귀무가설이 맞다는 가정하에, 귀무가설이 틀리다고 할 기준 영역 <br/>
    (즉, 관측된 통계량이 기각역에 포함되면 귀무가설 기각, 대립가설 채택) <br/>
- **채택역($1-\alpha$)** <br/>
  \: 귀무가설이 맞다는 가정하에, 귀무가설이 맞다고 할 기준 영역 <br/>
    (즉, 관측된 통계량이 채택역에 포함되면 귀무가설 채택, 대립가설 기각) <br/>
- **유의확률(p-value)** <br/>
  \: 귀무가설이 맞다는 전제하에, 관측된 통계량과 같거나 더욱 극단적인 통계량이 나올 확률 <br/>
    (즉, 기각역보다 유의확률이 작다면, 귀무가설 기각, 대립가설 채택)

> 기각역과 채택역은 분석가가 조정하는 부분이며, 유의확률은 자료로부터 계산된다. 
