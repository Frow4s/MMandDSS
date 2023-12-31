# Цель работы:
Знакомство с моделью Хольта-Уинтерса

# Задачи:
- Реализовать модель Хольта-Уинтерса
- Подобрать наилучшие параметры для выбранных данных

# Описание:

### Модель Хольта-Уинтерса (экспоненциальное сглаживание с трендом и сезонностью)

#### Уровень (Level):
Уровень (L) в момент времени t обновляется с учетом предыдущего значения уровня, тренда и сезонности.
$\[L_t = \alpha(Y_t - S_{t-m}) + (1 - \alpha)(L_{t-1} + T_{t-1})\]$
где:
- $\(L_t\)$ - текущее значение уровня,
- $\(\alpha\)$ - коэффициент сглаживания уровня,
- $\(Y_t\)$ - наблюдаемое значение временного ряда в момент времени t,
- $\(S_{t-m}\)$ - значение сезонной компоненты в момент времени t с учетом сезонного лага m,
- $\(L_{t-1}\)$ - предыдущее значение уровня,
- $\(T_{t-1}\)$ - предыдущее значение тренда.

#### Тренд (Trend):
Тренд (T) определяется как изменение уровня между соседними моментами времени.
$\[T_t = \beta(L_t - L_{t-1}) + (1 - \beta)T_{t-1}\]$
где:
- $\(T_t\)$ - текущее значение тренда,
- $\(\beta\)$ - коэффициент сглаживания тренда.

#### Сезонность (Seasonality):
Сезонная компонента (S) представляет собой паттерн или цикл, повторяющийся через определенные временные периоды.
$\[S_t = \gamma(Y_t - L_t) + (1 - \gamma)S_{t-m}\]$
где:
- $\(S_t\)$ - текущее значение сезонной компоненты,
- $\(\gamma\)$ - коэффициент сглаживания сезонности.

Модель Хольта-Уинтерса включает эти три уравнения для обновления уровня, тренда и сезонной компоненты, что позволяет учитывать тренд и сезонность при прогнозировании временных рядов.

# Заключение
Была реализована модель Хольта-Уинтерса на языке python, а также были подобраны наилучшие параметры с помощью библиотеки scipy.
