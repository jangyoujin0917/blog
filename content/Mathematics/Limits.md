---
tags:
  - Article/MAS
title: Limits | 극한
---
이 글은 과목 [[MAS101|미적분학 1]]의 일부입니다. 이 글은 현재 일변수함수 $f: \mathbb{R} \to \mathbb{R}$만을 다룹니다.

## 극한의 느슨한 정의
극한은 매우 직관적으로 다음과 같이 정의할 수 있다.

> [!Definition] 극한(Limit) - 직관적
> 지점 $c$를 포함하는 열린 구간 $I$에 대해서, 함수 $f$는 점 $c$를 제외한 열린 구간 $I$에서 정의되어 있다. $x$가 $c$에 가까워짐에 따라 $f$가 $L$에 한없이 가까워진다면, **$x$가 $c$로 다가갈 때 $f$의 극한**은 $L$이라고 할 수 있고, 기호로 다음과 같이 표현한다.
> 
> $$
> \lim_{x \to c}f(x)=L
> $$

하지만, 이 정의는 엄밀하지 못하다. $x$가 $c$에 가까워지는 것이 무엇인지, 또한 $f$가 $L$에 한없이 가까워지는 것이 무엇인지를 모르기에, 극한이 존재하는지, 유일한지에 대한 아무런 증명을 할 수 없다.

## 엡실론-델타 논법 (Epsilon-Delta Argument)
### 역사
극한을 정의하기 위한 다른 시도도 있었으나, 그 정의는 엄밀하지 못했다. 과학자 아이작 뉴턴은 유율법(fluxion)이라는 방법으로 미분을 하였으나, 극한이 아닌 미분소(infinitesimal)이라는, 0에 한없이 가깝지만 0은 아닌, 분수의 분모가 될 수 있는 기호를 사용하였다.[^1] 이 0은 아니지만 0에 한없이 가까워 무시할 수 있을 정도의 값은, 잘 정의되지 않았다.

극한은 수학자 오귀스탱 루이 코시가 정의한 엡실론-델타 논법 (Epsilon-Delta Argument)를 통해 엄밀하게 정의되었다.

### 정의
> [!Definition] 엡실론-델타 논법
> 지점 $c$를 포함하는 열린 구간 $I$에 대해서, 함수 $f$는 점 $c$를 제외한 열린 구간 $I$에서 정의되어 있다. $x$가 $c$로 접근할 때 $f$의 **극한**은, 모든 실수 $\varepsilon > 0$에 대해서, 다음을 만족하는 상응하는 실수 $\delta > 0$가 존재한다.
> $$
> 0 < |x-c| < \delta \Longrightarrow |f(x)-L|<\varepsilon
> $$
> 이 때, 이 극한을 다음과 같이 표기할 수 있다.
> $$
> \lim_{x \to c}f(x)=L
> $$
### 예제
다음 정의를 통해, 극한값이 맞는지를 증명할 수 있다. 모든 양수 $\varepsilon$에 대해, 그에 상응하는 $\delta$가 있음을 보이면 된다.
> [!Example]
> $\displaystyle\lim_{x \to 2} (2x+1)=5$임을 엡실론-델타 논법으로 증명하시오.


> 모든 실수 $\varepsilon>0$에 대해서, 다음을 만족하는 대응되는 $\delta>0$의 존재를 보이면 된다.
> 
> $$0<|x-2|<\delta \Longrightarrow |(2x+1)-5|<\varepsilon$$
> 
> $|(2x+1)-5| = |2x-4| = 2|x-2| < \varepsilon$
> 
> Let $\displaystyle\delta=\frac{\varepsilon}{2}$, $\displaystyle0<|x-2|<\delta=\frac{\varepsilon}{2} \Longrightarrow 2|x-2|<\varepsilon$
> 
> 모든 양수 $\varepsilon$에 대해 조건을 만족하는 $\delta=\varepsilon / 2$가 존재하므로, 주어진 극한값을 증명하였다.

## 극한 법칙 (Limit Laws)
 

[^1]: https://www.britannica.com/science/fluxion