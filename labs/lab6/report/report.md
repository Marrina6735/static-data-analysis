---
## Front matter
title: "Отчёт по лабораторной работе №6


Решение моделей в непрерывном и дискретном времени"
subtitle: "Статический анализ данных"
author: "Выполнила: Коняева Марина Александровна, 


НФИбд-01-21, 1032217044"



## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---


# Цели лабораторной работы

Освоить специализированных пакетов для решения задач в непрерывном и дискретном времени.

# Теоретическое введение 

![](111.png){ #fig:002 width=70% }

# Задачи лабораторной работы

1. Используя Jupyter Lab, повторите примеры из раздела 6.2.
2. Выполните задания для самостоятельной работы (раздел 6.4).

# Выполнение лабораторной работы

## Решение обыкновенных дифференциальных уравнений

![](111.png){ #fig:002 width=70% }

### Модель экспоненциального роста

1. Перед использованием пакетов следует их установить и подключить в Julia. 

подключаем необходимые пакеты:
import Pkg
Pkg.add("DifferentialEquations")
Pkg.add("Plots")

2. Рассмотрим пример использования этого пакета для решение уравнения модели экспоненциального роста, описываемую уравнением 𝑢′(𝑡) = 𝑎𝑢(𝑡), 𝑢(0) = 𝑢0, где 𝑎 — коэффициент роста. Предположим, что заданы следующие начальные данные 𝑎 = 0, 98, 𝑢(0) = 1, 0, 𝑡 ∈ [0; 1, 0]. Аналитическое решение модели (6.1) имеет вид: 𝑢(𝑡) = 𝑢0 exp(𝑎𝑡)𝑢(𝑡).

![Листинг](1.png){ #fig:002 width=70% }

![Модель экспоненциального роста](2.png){ #fig:002 width=70% }

3. Повторим аналогичный пример. При построении одного из графиков использовался вызов sol.t, чтобы захватить массив моментов времени. Массив решений можно получить, воспользовавшись sol.u. Если требуется задать точность решения, то можно воспользоваться параметрами abstol (задаёт близость к нулю) и reltol (задаёт относительную точность). По умолчанию эти параметры имеют значение abstol = 1e-6 и reltol = 1e-3.

![Листинг](3.png){ #fig:002 width=70% }

![Модель экспоненциального роста](4.png){ #fig:002 width=70% }

### Система Лоренца

![](112.png){ #fig:002 width=70% }

4. Повторим пример. Система (6.2) получена из системы уравнений Навье–Стокса и описывает движение воздушных потоков в плоском слое жидкости постоянной толщины при разложении скорости течения и температуры в двойные ряды Фурье с последующем усечением до первых-вторых гармоник. Решение системы неустойчиво на аттракторе, что не позволяет применять классические численные методы на больших отрезках времени, требуется использовать высокоточные вычисления.

![Листинг](5.png){ #fig:002 width=70% }

![Аттрактор Лоренца](6.png){ #fig:002 width=70% }

5. Повторим пример системы Лоренца, но при этом отключим интерполяцию.

![Листинг](7.png){ #fig:002 width=70% }

![Аттрактор Лоренца (интерполяция отключена)](8.png){ #fig:002 width=70% }

## Модель Лотки–Вольтерры

![](113.png){ #fig:002 width=70% }

6. Повторим пример реализации модели Лотки-Вольтерры.

![Листинг](9.png){ #fig:002 width=70% }

![Модель Лотки–Вольтерры](10.png){ #fig:002 width=70% }

7. Повторим пример: построим фазовый портрет для модели из пункта 6.

![Листинг и фазовый портрет](11.png){ #fig:002 width=70% }

## Задания для самостоятельного выполнения

1. Реализовать и проанализировать модель роста численности изолированной популяции (модель Мальтуса):
̇𝑥 = 𝑎𝑥, 𝑎 = 𝑏 − 𝑐.
где 𝑥(𝑡) — численность изолированной популяции в момент времени 𝑡, 𝑎 — коэффициент роста популяции, 𝑏 — коэффициент рождаемости, 𝑐 — коэффициент смертности.
Начальные данные и параметры задать самостоятельно и пояснить их выбор. Построить соответствующие графики (в том числе с анимацией).

Модель Мальтуса --- модель роста численности изолированной популяции, где изменение роста популяции контролируется численностью уже существующей популяции, домноженной на коэффициент $a$, который является разницей между рождаемостью и смертностью ($b-c$). Коэффициенты $b$ и $c$ было предложено выбрать самостоятельно, и я выставлю для системы значения $b=1.09$ и $c=1.134$ (что является соответственно коэффициентами рождаемости и смертности за январь-август в 2022 году в Центральном федеральном округе РФ). Изначальная численность населения ($39 433 556$ человек) также взята из статистики Росстата за 2022 год (с учётом переписи населения).

Модель Мальтуса подразумевает, что коэффициенты рождаемости и смертности не изменяются, так что если $b$ превышает $c$, численность популяции будет расти (и наоборот).

```
function Maltus!(du,u,p,t)
    du[1] = (p[1]-p[2])*u[1]
end
u0 = [39433556.0]
tspan = (0.0,100.0)
p = Float64[1.09, 1.134]
prob = ODEProblem(Maltus!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=1.0)
R1 = [tu[1] for tu in sol.u]
plot(sol.t, R1, title="Модель Мальтуса", xaxis="Время",yaxis="Численность",label="u(t)", c=:blue)
```

![Модель Мальтуса](12.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(sol.t)
    plot(sol.t[1:i], R1[1:i], title="Логистическая модель роста популяции", xaxis="Время",yaxis="Численность",label="u(t)", c=:blue)
end
gif(anim, "presentation//image//2.gif")
```

![Модель Мальтуса](1.gif){ #fig:002 width=70% }

2. Реализовать и проанализировать логистическую модель роста популяции, заданную уравнением:
̇𝑥 = 𝑟𝑥 (1 − 𝑥 𝑘) , 𝑟 > 0, 𝑘 > 0,
𝑟 — коэффициент роста популяции, 𝑘 — потенциальная ёмкость экологической системы (предельное значение численности популяции). Начальные данные и параметры задать самостоятельно и пояснить их выбор. Построить соответствующие графики (в том числе с анимацией).

```
function LogModPop!(du,u,p,t)
    du[1] = p[1]*u[1]*(1-u[1]/p[2])
end
u0 = [39433556.0]
tspan = (0.0,100.0)
p = Float64[1.09, 15e7]
prob = ODEProblem(LogModPop!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=1.0)
R1 = [tu[1] for tu in sol.u]
plot(sol.t, R1, title="Логистическая модель роста популяции", xaxis="Время",yaxis="Численность",label="u(t)", c=:blue)
```

![Логистическая модель роста популяции](13.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(sol.t)
    plot(sol.t[1:i], R1[1:i], title="Логистическая модель роста популяции", xaxis="Время",yaxis="Численность",label="u(t)", c=:blue)
end
gif(anim, "presentation//image//2.gif")
```

![Логистическая модель роста популяции](2.gif){ #fig:002 width=70% }

3. Модель эпидемии Кермака–Маккендрика (SIR-модель):

  Реализовать и проанализировать SIR-модель:

  ```
  ẋₛ = -βis
  ẋᵢ = βis - νi
  ẋᵣ = νi
  ```

  где:

  * s(t) — численность восприимчивых индивидов
  * i(t) — численность инфицированных индивидов
  * r(t) — численность переболевших индивидов
  * β — коэффициент интенсивности контактов с инфицированием
  * ν — коэффициент интенсивности выздоровления

  ẋₛ + ẋᵢ + ẋᵣ = 0 (численность популяции постоянна).

  Самостоятельно задать начальные данные и параметры, объяснив свой выбор. Построить графики численности каждой группы со временем (включая анимацию).

```
function SIR!(du,u,p,t)
    du[1] = -p[1]*u[1]*u[2] # S
    du[2] = p[1]*u[2]*u[1]-p[2]*u[2] # I
    du[3] = p[2]*u[2] # R
end
u0 = [39433553.0, 3.0, 0.0]
tspan = (0.0,20.0)
p = Float64[0.3,0.7]
prob = ODEProblem(SIR!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=0.01)
R1 = [tu[1] for tu in sol.u]
R2 = [tu[2] for tu in sol.u]
R3 = [tu[3] for tu in sol.u]
plot(sol.t, R1, title="SIR", xaxis="Время",yaxis="Численность",label="Susceptable", c=:green, leg=:topright)
plot!(sol.t, R2, title="SIR", label="Infected", c=:red, leg=:topright)
plot!(sol.t, R3, label="Recovered", c=:blue, leg=:topright)
```

![SIR](14.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(sol.t)
    plot(sol.t[1:i], R1[1:i], title="SIR", xaxis="Время",yaxis="Численность",label="Susceptable", c=:green, leg=:topright)
    plot!(sol.t[1:i], R2[1:i], title="SIR", label="Infected", c=:red, leg=:topright)
    plot!(sol.t[1:i], R3[1:i], label="Recovered", c=:blue, leg=:topright)
end
gif(anim, "presentation//image//3.gif")
```

![SIR](3.gif){ #fig:002 width=70% }

4.  Реализовать и проанализировать модель SEIR (Susceptible-Exposed-Infected-Removed):

  ```
  ẋₛ(t) = -β/N * s(t)i(t)
  ẋₑ(t) = β/N * s(t)i(t) - δe(t)
  ẋᵢ(t) = δe(t) - γi(t)
  ẋᵣ(t) = γi(t)
  s(t) + e(t) + i(t) + r(t) = N
  ```

  Сравнить результаты с SIR-моделью.

```
function SEIR!(du,u,p,t)
    betta, delta, gamma, N = p
    s, e, i, r = u
    du[1] = -betta / N * s * i
    du[2] = betta / N * s * i - delta * e
    du[3] = delta * e - gamma * i
    du[4] = gamma * i
end
u0 = [0.98, 0.02, 0.0, 0.0]
tspan = (0.0,200.0)
p = Float64[0.8,0.4,0.3,1.0]
prob = ODEProblem(SEIR!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=0.1)
R1 = [tu[1] for tu in sol.u]
R2 = [tu[2] for tu in sol.u]
R3 = [tu[3] for tu in sol.u]
R4 = [tu[4] for tu in sol.u]
plot(sol.t, R1, title="SEIR", xaxis="Время",yaxis="Численность",label="Susceptable", c=:green, leg=:topright)
plot!(sol.t, R2, label="Exposed", c=:orange, leg=:topright)
plot!(sol.t, R3, label="Infected", c=:red, leg=:topright)
plot!(sol.t, R4, label="Recovered", c=:blue, leg=:topright)
```

![SEIR](15.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(sol.t)
    plot(sol.t[1:i], R1[1:i], title="SEIR", xaxis="Время",yaxis="Численность",label="Susceptable", c=:green, leg=:topright)
    plot!(sol.t[1:i], R2[1:i], label="Exposed", c=:orange, leg=:topright)
    plot!(sol.t[1:i], R3[1:i], label="Infected", c=:red, leg=:topright)
    plot!(sol.t[1:i], R4[1:i], label="Recovered", c=:blue, leg=:topright)
end
gif(anim, "presentation//image//4.gif")
```

![SEIR](4.gif){ #fig:002 width=70% }

5. Дискретная модель Лотки–Вольтерры:

  Для дискретной модели:

  ```
  X₁(t + 1) = aX₁(t)(1 - X₁(t)) - X₁(t)X₂(t)
  X₂(t + 1) = -cX₂(t) + dX₁(t)X₂(t)
  ```

  с начальными данными a = 2, c = 1, d = 5 найти точку равновесия. Получить и сравнить аналитическое и численное решения. Изобразить численное решение на фазовом портрете.

```
using NLsolve
# Аналитическое решение
function find_equilibrium(a, c, d)
    function system!(du, u)
        du[1] = a*u[1]*(1-u[1]) - u[1]*u[2]
        du[2] = -c*u[2] + d*u[1]*u[2]
    end

    initial_guess = [0.5, 0.5]
    result = nlsolve(system!, initial_guess)

    equilibrium_point = result.zero
    return equilibrium_point
end
# Численное решение
function LotkiVolterry(a, c, d, x1_0, x2_0, dt, num_steps)
    x1 = x1_0
    x2 = x2_0
    results = [(x1, x2)]

    for _ in 1:num_steps
        x1_new = x1 + dt * (a * x1 * (1 - x1) - x1 * x2)
        x2_new = x2 + dt * (-c * x2 + d * x1 * x2)
        x1, x2 = x1_new, x2_new
        push!(results, (x1, x2))
    end  
    
    return results
end

a = 2.0
c = 1.0
d = 5.0
x1_0 = 0.15
x2_0 = 0.25
dt = 0.01
num_steps = 10000

results = LotkiVolterry(a, c, d, x1_0, x2_0, dt, num_steps)
R1 = [x[1] for x in results]
R2 = [x[2] for x in results]

equilibrium = find_equilibrium(2,1,5)

plot(R1, R2, title="Лотки-Вольтерры (фазовый портрет)", leg=:topright)
scatter!([equilibrium[1]], [equilibrium[2]], color="red", label="Точка равновесия")
```

![модель Лотки–Вольтерры фазовый портрет](16.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(R1)
    plot(R1[1:i], R2[1:i], title="Лотки-Вольтерры (фазовый портрет)", leg=:topright)
    scatter!([equilibrium[1]], [equilibrium[2]], color="red", label="Точка равновесия")
end
gif(anim, "presentation//image//5.gif")
```

![модель Лотки–Вольтерры фазовый портер](5.gif){ #fig:002 width=70% }

6. Модель отбора на основе конкурентных отношений (Julia):

  Реализовать модель:

  ```
  ẋ = αx - βxy
  ẏ = αy - βxy
  ```

  Самостоятельно задать начальные данные и параметры, объяснив свой выбор. Построить графики и фазовый портрет (включая анимацию).

```
function KonkOtn!(du,u,p,t)
    du[1] = p[1] * u[1] - p[2] * u[1] * u[2]
    du[2] = -p[1] * u[2] + p[2] * u[1] * u[2]
end
u0 = [16.0,7.0]
tspan = (0.0,100.0)
p = Float64[0.02, 0.04]
prob = ODEProblem(KonkOtn!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=0.1)
R1 = [tu[1] for tu in sol.u]
R2 = [tu[2] for tu in sol.u]
plot(sol.t, R1, title="Конкурентные отношения", xaxis="Время",yaxis="Значение",label="x", c=:green, leg=:topright)
plot!(sol.t, R2, label="y", c=:orange, leg=:topright)
```

![Конкурентные отношения](17.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(R1)
    plot(sol.t[1:i], R1[1:i], title="Конкурентные отношения", xaxis="Время",yaxis="Значение",label="x", c=:green, leg=:topright)
    plot!(sol.t[1:i], R2[1:i], label="y", c=:orange, leg=:topright)
end
gif(anim, "presentation//image//6.gif")
```

![Конкурентные отношения](6.gif){ #fig:002 width=70% }

```
plot(R1, R2, title="Конкурентные отношения (фазовый портрет)", leg=:topright)
```

![Фазовый портрет](18.png){ #fig:002 width=70% }

7. Консервативный гармонический осциллятор (Julia):

  Реализовать модель:

  ```
  ẍ + ω₀²x = 0, x(t₀) = x₀, ẋ(t₀) = y₀
  ```

  Самостоятельно задать начальные параметры, объяснив свой выбор. Построить графики и фазовый портрет (включая анимацию).

```
function KGO!(du,u,p,t)
    du[1] = u[2]
    du[2] = -p[1]^2 * u[1]
end
u0 = [0.0, 1.0]
tspan = (0.0,10.0)
p = Float64[3.0]
prob = ODEProblem(KGO!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=0.1)
R1 = [tu[1] for tu in sol.u]
R2 = [tu[2] for tu in sol.u]
plot(sol.t, R1, title="Консервативный гармонический осциллятор", xaxis="Время",yaxis="Значение",label="x(t)", c=:green, leg=:topright)
plot!(sol.t, R2, label="v(t)", c=:orange, leg=:topright)
```

![Консервативный гармонический осциллятор](19.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(R1)
    plot(sol.t[1:i], R1[1:i], title="Консервативный гармонический осциллятор", xaxis="Время",yaxis="Значение",label="x(t)", c=:green, leg=:topright)
    plot!(sol.t[1:i], R2[1:i], label="v(t)", c=:orange, leg=:topright)
end
gif(anim, "presentation//image//7.gif")
```

![Консервативный гармонический осциллятор](7.gif){ #fig:002 width=70% }

```
plot(R1, R2, title="Консервативный гармонический осциллятор (фазовый портрет)", leg=:topright)
```

![Фазовый портрет](20.png){ #fig:002 width=70% }

8. Свободные колебания гармонического осциллятора (Julia):

  Реализовать модель затухающих колебаний:

  ```
  ẍ + 2γẋ + ω₀²x = 0, x(t₀) = x₀, ẋ(t₀) = y₀
  ```

  где γ — параметр затухания. Самостоятельно задать начальные параметры, объяснив свой выбор. Построить графики и фазовый портрет (включая анимацию).

```
function GO!(du,u,p,t)
    du[1] = u[2]
    du[2] = -2.0*p[2]*u[2] - p[1]^2*u[1]
end
u0 = [0.0, 1.0]
tspan = (0.0,10.0)
p = Float64[4.0, 0.2]
prob = ODEProblem(GO!,u0,tspan,p)
sol = solve(prob,abstol=1e-6,reltol=1e-6, saveat=0.1)
R1 = [tu[1] for tu in sol.u]
R2 = [tu[2] for tu in sol.u]
plot(sol.t, R1, title="Гармонический осциллятор", xaxis="Время",yaxis="Значение",label="x(t)", c=:green, leg=:topright)
plot!(sol.t, R2, label="v(t)", c=:orange, leg=:topright)
```

![Гармонический осциллятор](21.png){ #fig:002 width=70% }

```
anim = @animate for i in 1:length(R1)
    plot(sol.t[1:i], R1[1:i], title="Гармонический осциллятор", xaxis="Время",yaxis="Значение",label="x(t)", c=:green, leg=:topright)
    plot!(sol.t[1:i], R2[1:i], label="v(t)", c=:orange, leg=:topright)
end
gif(anim, "presentation//image//8.gif")
```

![Гармонический осциллятор](4.gif){ #fig:002 width=70% }

```
plot(R1, R2, title="Гармонический осциллятор (фазовый портрет)", leg=:topright)
```

![Фазовый портрет](22.png){ #fig:002 width=70% }

# Выводы по проделанной работе

## Вывод

В результате выполнения работы мы освоили специализированные пакеты для решения задач в непрерывном и дискретном времени.
Были записаны скринкасты выполнения , создания отчета, презентации и защиты лабораторной работы.

# Список литературы

- Julia: https://ru.wikipedia.org/wiki/Julia
- https://julialang.org/packages/
- https://juliahub.com/ui/Home
- https://juliaobserver.com/
- https://github.com/svaksha/Julia.jl
