---
title: Limits | 극한
tags:
  - Article/MAS
  - MAS101
---
![[MAS101]]

이 글은 현재 MAS101 미적분학 1에 맞춰 일변수함수 $f: \mathbb{R} \to \mathbb{R}$만을 다룹니다.

## 극한의 느슨한 정의
극한은 매우 직관적으로 다음과 같이 정의할 수 있다.

> [!note] 극한(Limit) - 직관적
> 지점 $c$를 포함하는 열린 구간 $I$에 대해서, 함수 $f$는 점 $c$를 제외한 열린 구간 $I$에서 정의되어 있다. $x$가 $c$에 가까워짐에 따라 $f$가 $L$에 한없이 가까워진다면, **$x$가 $c$로 다가갈 때 $f$의 극한**은 $L$이라고 할 수 있고, 기호로 다음과 같이 표현한다.
> 
> $$
> \lim_{x \to c}f(x)=L
> $$

하지만, 이 정의는 엄밀하지 못하다. $x$가 $c$에 가까워지는 것이 무엇인지, 또한 $f$가 $L$에 한없이 가까워지는 것이 무엇인지를 모르기에, 극한이 존재하는지, 유일한지에 대한 아무런 증명을 할 수 없다.

## Epsilon-Delta Argument | 엡실론-델타 논법
### 역사
극한을 정의하기 위한 다른 시도도 있었으나, 그 정의는 엄밀하지 못했다. 과학자 아이작 뉴턴은 유율법(fluxion)이라는 방법으로 미분을 하였으나, 극한이 아닌 미분소(infinitesimal)이라는, 0에 한없이 가깝지만 0은 아닌, 분수의 분모가 될 수 있는 기호를 사용하였다.[^1] 이 0은 아니지만 0에 한없이 가까워 무시할 수 있을 정도의 값은, 잘 정의되지 않았다.

극한은 수학자 오귀스탱 루이 코시가 정의한 엡실론-델타 논법(Epsilon-Delta Argument)을 통해 엄밀하게 정의되었다.

### 정의
> [!note] 엡실론-델타 논법
> 지점 $c$를 포함하는 열린 구간 $I$에 대해서, 함수 $f$는 (점 $c$를 제외한) 열린 구간 $I$에서 정의되어 있다. $x$가 $c$로 접근할 때 $f$의 **극한**이 $L$이면, 모든 실수 $\varepsilon > 0$에 대해서, 다음을 만족하는 상응하는 실수 $\delta > 0$가 존재한다.
> $$
> 0 < |x-c| < \delta \Longrightarrow |f(x)-L|<\varepsilon
> $$
> 이 때, 이 극한을 다음과 같이 표기할 수 있다.
> $$
> \lim_{x \to c}f(x)=L
> $$

이 정의를 이용하여 [[Limit Laws|극한 법칙]]을 유도할 수 있다.
### 예제
다음 정의를 통해, 극한값의 존재와 값이 맞는지를 증명할 수 있다. 모든 양수 $\varepsilon$에 대해, 그에 상응하는 양수 $\delta$가 있음을 보이면 된다.
> [!Example]
> $\displaystyle\lim_{x \to 2} (2x+1)=5$임을 엡실론-델타 논법으로 증명하시오.
> > 모든 실수 $\varepsilon>0$에 대해서, 다음을 만족하는 대응되는 $\delta>0$의 존재를 보이면 된다.
> >
> > $$0<|x-2|<\delta \Longrightarrow |(2x+1)-5|<\varepsilon$$
> >
> > $|(2x+1)-5| = |2x-4| = 2|x-2| < \varepsilon$
> >
> > Let $\displaystyle\delta=\frac{\varepsilon}{2}$, $\displaystyle0<|x-2|<\delta=\frac{\varepsilon}{2} \Longrightarrow 2|x-2|<\varepsilon$
> >
> > 모든 양수 $\varepsilon$에 대해 조건을 만족하는 $\delta=\varepsilon / 2$가 존재하므로, 주어진 극한을 증명하였다.
## One-sided Limit | 좌극한과 우극한
### 정의
 위에서 정의한 극한은 점 $c$를 포함하는 열린 구간에서 정의된 함수를 사용하여서, $x$가 $c$에 양쪽으로 접근하는 상황이었다. 그러나, 점 $c$에서 한쪽만 정의되어 있는 함수에 대해서도, 좌극한과 우극한을 사용하여 극한을 정의할 수 있다.
 
> [!note] 좌극한
> 열린 구간 $a<x<c$에서 정의되어 있는 함수 $f$에 대해서, $x$가 $c$로 접근할 때 $f$의 **좌극한**이 $L$이면, 모든 실수 $\varepsilon > 0$에 대해서, 다음을 만족하는 상응하는 실수 $\delta > 0$가 존재한다.
> $$
> c-\delta < x < c \Longrightarrow |f(x)-L|<\varepsilon
> $$
> 이 때, 이 극한을 다음과 같이 표기할 수 있다.
> $$
> \lim_{x \to c^{-}}f(x)=L
> $$

> [!Definition] 우극한
> 열린 구간 $c<x<b$에서 정의되어 있는 함수 $f$에 대해서, $x$가 $c$로 접근할 때 $f$의 **우극한**이 $L$이면, 모든 실수 $\varepsilon > 0$에 대해서, 다음을 만족하는 상응하는 실수 $\delta > 0$가 존재한다.
> $$
> c < x < c+\delta \Longrightarrow |f(x)-L|<\varepsilon
> $$
> 이 때, 이 극한을 다음과 같이 표기할 수 있다.
> $$
> \lim_{x \to c^{+}}f(x)=L
> $$
### 정리
좌극한과 우극한의 정의에 따라, 다음 정리가 참이다.

> [!info] 정리
> 지점 $c$를 포함하는 열린 구간 $I$에 대해서, 함수 $f$는 점 $c$를 제외한 열린 구간 $I$에서 정의되어 있다. 이때, $c$에서 함수 $f(x)$의 극한이 $L$이라는 것은 $c$에서의 함수 $f(x)$의 좌극한과 우극한이 모두 $L$로 존재한다는 것과 동치이다. 즉, 수식으로 쓰면 다음과 같다.
> $$
> \lim_{x \to c}f(x)=L \Longleftrightarrow \lim_{x \to c^{-}}f(x)=\lim_{x \to c^{+}}f(x)=L
> $$
### 예제
> [!Example]
> $\displaystyle\lim_{x \to 0^{+}} \sqrt{x}=0$임을 엡실론-델타 논법으로 증명하시오.
> > 모든 실수 $\varepsilon>0$에 대해서, 다음을 만족하는 대응되는 $\delta>0$의 존재를 보이면 된다.
> >
> > $$0<x<\delta \Longrightarrow |\sqrt{x}|<\varepsilon$$
> >
> > Let $\displaystyle\delta={\varepsilon}^{2}$, $\displaystyle0<x<\delta={\varepsilon}^{2} \Longrightarrow |\sqrt{x}|=\sqrt{x}<\sqrt{\varepsilon^{2}}=\varepsilon$
> >
> > 모든 양수 $\varepsilon$에 대해 조건을 만족하는 $\delta=\varepsilon^{2}$가 존재하므로, 주어진 극한을 증명하였다.
## Limits involving Infinity | 무한대를 포함한 극한
### 무한대로 접근하는 극한
 또한, $x$가 양의 무한대($+\infty$)나 음의 무한대($-\infty$)로 접근할 때의 극한도 정의할 수 있다.
 
> [!note] $x$가 양의 무한대로 접근
> 열린 구간 $a<x<\infty$에서 정의되어 있는 함수 $f$에 대해서, $x$가 양의 무한대로 접근할 때 $f$의 **극한**이 $L$이면, 모든 실수 $\varepsilon > 0$에 대해서, 다음을 만족하는 상응하는 실수 $M$이 존재한다.
> $$
> x > M \Longrightarrow |f(x)-L|<\varepsilon
> $$
> 이 때, 이 극한을 다음과 같이 표기할 수 있다.
> $$
> \lim_{x \to \infty}f(x)=L
> $$

> [!note] $x$가 음의 무한대로 접근
> 열린 구간 $-\infty<x<b$에서 정의되어 있는 함수 $f$에 대해서, $x$가 음의 무한대로 접근할 때 $f$의 **극한**이 $L$이면, 모든 실수 $\varepsilon > 0$에 대해서, 다음을 만족하는 상응하는 실수 $N$이 존재한다.
> $$
> x < N \Longrightarrow |f(x)-L|<\varepsilon
> $$
> 이 때, 이 극한을 다음과 같이 표기할 수 있다.
> $$
> \lim_{x \to -\infty}f(x)=L
> $$

이 경우에도 일반적인 [[Limits#Epsilon-Delta Argument 엡실론-델타 논법|엡실론-델타 논법]]과 같은 형태의 극한 법칙을 유도할 수 있다.

### 양의 무한대/음의 무한대로 발산



[^1]: https://www.britannica.com/science/fluxion