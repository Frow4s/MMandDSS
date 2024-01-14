# Цель работы:
Развитие навыков обработки экспертных оценок, заданных для объектов числовыми значениями

# Задачи:
- Реализовать программу на языке python для вычисления обобщенных экспертных оценок по объектам и коэффициенты компетентности экспертов

# Описание:

Подход 1 от ChatGPT:

````
function calculate_aggregated_ratings(expert_ratings):
    num_objects, num_experts = dimensions of expert_ratings matrix

    // Инициализация вектора коэффициентов компетентности
    competency_factors = ones(num_experts)

    // Максимальное количество итераций (можно изменить по необходимости)
    max_iterations = 100

    for iteration in range(max_iterations):
        // Вычисление средних оценок объектов
        object_ratings = sum(expert_ratings * competency_factors) / sum(competency_factors)

        // Обновление коэффициентов компетентности
        new_competency_factors = sum(expert_ratings.transpose() * object_ratings) / sum((expert_ratings.transpose())^2)

        // Проверка условия выхода: если новые коэффициенты почти совпадают со старыми
        if allclose(new_competency_factors, competency_factors, rtol=1e-6):
            break

        competency_factors = new_competency_factors

    // Вычисление обобщенных экспертных оценок
    aggregated_ratings = object_ratings

    return aggregated_ratings, competency_factors
````

Подход 2 из методички:
````
// Предполагаем, что expert_ratings_matrix - это матрица экспертных оценок
// @ обозначает умножение матриц (в коде используется оператор @)

// Вычисление матрицы B
B = expert_ratings_matrix @ expert_ratings_matrix.T

// Вычисление матрицы C
C = expert_ratings_matrix.T @ expert_ratings_matrix

// Вычисление обобщенных экспертных оценок
// для коэффициентов компетентности экспертов

// Вычисление произведения по столбцам матрицы B
product_B = product(B, axis=0)

// Вычисление корня B.shape[0]-ой степени для каждого элемента произведения
rooted_product_B = product_B ** (1 / B.shape[0])

// Вычисление суммы корней произведения
sum_rooted_product_B = sum(rooted_product_B)

// Вычисление коэффициентов компетентности экспертов
competency_factors_B = rooted_product_B / sum_rooted_product_B

// Вывод коэффициентов компетентности
print("Коэффициенты компетентности экспертов:")
print(competency_factors_B)
````

# Заключение
Была реализована программа на языке python для вычисления обобщенных экспертных оценок по объектам и коэффициенты компетентности экспертов
