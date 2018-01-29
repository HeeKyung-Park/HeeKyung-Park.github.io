---
layout: post
title: Chi-square test (카이제곱-검정)
categories : [Statistics]
comments: true
tags : 
- Basic Statistics
---

<div class="message">
  반응변수가 범주형일 때, 관찰된 빈도가 기대되는 빈도와 차이가 있는지를 검정해보자.
</div>

## <span style='color:#6a9fb5'> 카이제곱-검정 </span>
\- 각 변수(범주형)에 대한 집단의 분포가 독립인지를 검정 <br/>
\- 관찰도수와 기대도수의 차를 이용하여 카이제곱값을 구하여 검정 <br/>

<div class="message">
  <strong> Example> </strong> <br/>
  어느 인터넷 쇼핑몰을 방문한 100명을 조사해보니 구매집단이 75명(75%)이고 비구매집단이 (25%)였다. 이 때, 각 집단에 대한 여성과 남성의 비율은 위의 표와 같다. 여성과 남성의 구매 빈도가 다르다고 할 수 있는지 검정해보자. 
</div>

<style>
.table01 {
    border-top: 1.5px solid #ccc;
}
.table01 th {
    vertical-align: top;
    border-bottom: 1.5px solid #ccc;
}
.table01 td {
    vertical-align: top;
    border-bottom: 1.5px solid #ccc;
}
</style>


<table class="table01" style="width:80%; margin-left:auto; margin-right:auto;" >
	<tr bgcolor="#5a86c3" style="color:#FFFFFF">
		<th>성별</th>
		<th>구매집단</th>
		<th>비구매집단</th>
		<th>합계</th>
	</tr>
	<tr>
		<th>남성</th>
		<th>30</th>
		<th>20</th>
		<th>50</th>
	</tr>
	<tr>
		<th>여성</th>
		<th>45</th>
		<th>5</th>
		<th>50</th>
	</tr>
	<tr>
		<th>합계</th>
		<th>75</th>
		<th>25</th>
		<th>100</th>
	</tr>
</table>


\: 성별에 따라 차이가 나지 않는다면, 남성, 여성의 구별 없이 구매집단은 50명의 75%인 37.5명, 비구매집단은 50명의 25%인 12.5명 정도로 기대할 수 있다. <span style="color:red"> 카이제곱검정은 관측도수와 기대도수의 차이를 통해 변수사이의 독립성을 검정한다.</span> (즉, 성별과 구매여부가 독립인가를 검정 ) <br/>
<br/>

<strong> 가설 </strong>
- $H_0$ : 성별과 구매여부는 연관성이 없다. (=독립이다.) <br/>
- $H_1$ : 성별과 구매여부는 연관성이 있다. (=독립이 아니다.) <br/>

<strong> 검정통계량 </strong>

$$\chi^2 = \sum\frac{(O-E)^2}{E}$$

- $O : $ 관측도수 <br/>
- $E : $ 기대도수 <br/>

<strong> 자유도 </strong>

$$d.f = (ncol-1)(nrow-1)$$

- $ncol : $ colunm의 개수 (합계 미포함)
- $nrow : $ row의 개수 (합계 미포함)


<br/>
각 셀에 기대빈도를 표현한 표는 아래와 같다.<br/>

<table class="table01" style="width:80%; margin-left:auto; margin-right:auto;" >
	<tr bgcolor="#5a86c3" style="color:#FFFFFF">
		<th>성별</th>
		<th>구매집단</th>
		<th>비구매집단</th>
		<th>합계</th>
	</tr>
	<tr>
		<th>남성</th>
		<th>30(37.5)</th>
		<th>20(12.5)</th>
		<th>50</th>
	</tr>
	<tr>
		<th>여성</th>
		<th>45(37.5)</th>
		<th>5(12.5)</th>
		<th>50</th>
	</tr>
	<tr>
		<th>합계</th>
		<th>75</th>
		<th>25</th>
		<th>100</th>
	</tr>
	<tfoot>
        <tr>
            <td colspan="4">* 남성의 구매집단 기대도수 = 100 × 50/100 × 75/100 = 37.5 <br/>
            * 여성의 비구매집단 기대도수 = 100 × 50/100 × 25/100 = 12.5</td>
        </tr>
    </tfoot>
</table>

- 검정통계량 <br/>
$$\chi^2 = \sum\frac{(O-E)^2}{E} = \frac{(30-37.5)^2}{37.5}+\frac{(20-12.5)^2}{12.5}+\frac{(45-37.5)^2}{37.5}+\frac{(5-12.5)^2}{12.5}=10.453$$

- 자유도 <br/>
$$d.f = (ncol-1)(nrow-1) = (2-1)(2-1) = 1$$

<p align="center"><img width="250" height="auto" src="https://i.imgur.com/Ayc4Lh1.png"></p>

- p-value  <br/>
$$p = Pr[X \geq \chi^2] = Pr[X \geq 12] = 0.000532 $$

\: 유의수준 0.05에서 귀무가설을 기각, 대립가설(성별과 구매여부는 독립이 아니다. 성별에 따른 구매여부의 분포가 차이가 있다.)를 채택


<strong> 예제 R 코드 </strong>

<div class="colorscripter-code" style="color:#010101; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#fafafa; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #e5e5e5"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#666; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#010101; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">Mat&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">&lt;</span><span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>&nbsp;matrix(c(<span style="color:#0099cc">30</span>,&nbsp;<span style="color:#0099cc">20</span>,&nbsp;<span style="color:#0099cc">45</span>,&nbsp;<span style="color:#0099cc">5</span>),&nbsp;ncol<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span><span style="color:#0099cc">2</span>,&nbsp;byrow<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>TRUE)</div><div style="padding:0 6px; white-space:pre; line-height:130%">colnames(Mat)&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">&lt;</span><span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>&nbsp;c(<span style="color:#63a35c">"구매"</span>,&nbsp;<span style="color:#63a35c">"비구매"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">rownames(Mat)&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">&lt;</span><span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>&nbsp;c(<span style="color:#63a35c">"남성"</span>,&nbsp;<span style="color:#63a35c">"여성"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">Xsq&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">&lt;</span><span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>&nbsp;chisq.test(Mat,&nbsp;correct<span style="color:#0086b3"></span><span style="color:#a71d5d">=</span>FALSE))&nbsp;<span style="color:#999999">#&nbsp;No&nbsp;continuity&nbsp;correction</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">sum((Xsq$observed&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">-</span>&nbsp;Xsq$expected)^<span style="color:#0099cc">2</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#a71d5d">/</span>&nbsp;Xsq$expected)&nbsp;&nbsp;<span style="color:#999999">#&nbsp;검정통계량</span></div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#e5e5e5; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>