# 🌐 Language / Язык

[🇬🇧 English](#english) | [🇷🇺 Русский](#russian)

---

## <a name="russian"></a>

# Bank Churn Analysis

## 📌 О проекте

Проект выполнен в рамках курса **"Предиктивные модели и прикладная аналитика"** (модуль SQL майнора НИУ ВШЭ, 3 семестр).

**Цель:** анализ данных об оттоке клиентов банка и представление результатов в компактной и понятной форме (отчёт + дашборд).

**Задачи:**
- Подключение к базе данных ClickHouse (только необходимые данные)
- Построение графика оттока по возрастным группам
- Обучение модели логистической регрессии для предсказания оттока
- Создание интерактивного дашборда (Shiny) с фильтром по возрасту

## 📁 Содержимое репозитория

| Файл | Описание |
|------|----------|
| `analysis.Rmd` | Исходный код на R (пароль удалён) |
| `report.html` | HTML-отчёт с анализом и выводами (код скрыт, кнопка *Show/hide code*) |
| `Задание.png` | Скриншот задания |
| `Оценка+отзыв.png` | Скриншот оценки и отзыва |

> ⚠️ **Важно:** 
> - Пароль от ClickHouse удалён из кода в целях безопасности
> - **Rmd-код не может быть выполнен**, но результаты сохранены в HTML-отчёте

## 🔍 Что было сделано

### Подключение к базе данных
- Использован ClickHouseHTTP для подключения к удалённой БД
- Данные загружаются точечными SQL-запросами (без перегрузки окружения)

### Анализ оттока
- Построен график распределения ушедших клиентов по возрастным группам (10-летние интервалы)

### Моделирование
- **Модель:** логистическая регрессия
- **Признаки:** Age, CreditScore, Balance, NumOfProducts, HasCrCard, IsActiveMember
- **Целевая переменная:** Exited (1 — ушёл, 0 — остался)

**Метрики качества:**
| Метрика | Значение |
|---------|----------|
| Accuracy | ~0.81 |
| AUC-ROC | ~0.85 |

### Пример работы модели
Для конкретного клиента модель предсказывает вероятность оттока с выводом рекомендации (группа риска / надёжный клиент).

### Дашборд (Shiny)
- **Одна страница, без вкладок**
- **Интерактивный график:** отток по возрастным группам (работает при непосредственном запуске кода)
- **Элемент управления:** слайдер для выбора возрастного диапазона

> ⚠️ Дашборд требует запуска R-сервера и не работает в статическом HTML-файле.

## 🎓 Оценка

**Оценка:** 9.1 / 10.0

![Оценка и отзыв](Оценка+отзыв.png)

## 🚀 Как просмотреть

1. **Отчёт:** откройте `report.html` в браузере
2. **Код:** нажмите кнопку *Show/hide code* в правом верхнем углу отчёта
3. **Дашборд:** требует запуска RStudio (не работает в статическом HTML). Если пользователь имеет аккаунт на ClickHouse и запустит код из своего аккаунта, дашборд будет работать локально.

## 🛠 Инструменты

- R
- DBI, ClickHouseHTTP (подключение к БД)
- ggplot2 (визуализация)
- caret, pROC (моделирование и метрики)
- shiny (интерактивный дашборд)

## 📌 Автор

Подолин Дмитрий  
НИУ ВШЭ, курс "Предиктивные модели и прикладная аналитика"

---

## <a name="english"></a>

# Bank Churn Analysis

## 📌 About the project

The project was completed as part of the **"Predictive Modeling and Applied Analytics"** course (SQL module, HSE Minor, 3rd semester).

**Goal:** analysis of bank customer churn data and presentation of results in a compact and understandable form (report + dashboard).

**Tasks:**
- Connecting to a ClickHouse database (only necessary data)
- Constructing a churn distribution chart by age groups
- Training a logistic regression model to predict churn
- Creating an interactive Shiny dashboard with an age filter

## 📁 Repository contents

| File | Description |
|------|-------------|
| `analysis.Rmd` | R source code (password removed) |
| `report.html` | HTML report with analysis and conclusions (code hidden, *Show/hide code* button) |
| `Задание.png` | Screenshot of the assignment |
| `Оценка+отзыв.png` | Screenshot of the grade and feedback |

> ⚠️ **Important:** 
> - The ClickHouse password has been removed from the code for security reasons
> - **The Rmd code cannot be executed**, but the results are preserved in the HTML report

## 🔍 What was done

### Database connection
- Used ClickHouseHTTP to connect to a remote database
- Data is loaded via targeted SQL queries (without overloading the environment)

### Churn analysis
- Constructed a chart of churned customer distribution by age groups (10-year intervals)

### Modeling
- **Model:** logistic regression
- **Features:** Age, CreditScore, Balance, NumOfProducts, HasCrCard, IsActiveMember
- **Target variable:** Exited (1 — churned, 0 — stayed)

**Quality metrics:**
| Metric | Value |
|---------|----------|
| Accuracy | ~0.81 |
| AUC-ROC | ~0.85 |

### Model example
For a specific client, the model predicts churn probability with a recommendation (risk group / reliable client).

### Dashboard (Shiny)
- **One page, no tabs**
- **Interactive chart:** churn by age groups (works when running the code directly)
- **Control element:** slider for selecting age range

> ⚠️ The dashboard requires an R server to run and does not work in a static HTML file.

## 🎓 Grade

**Grade:** 9.1 / 10.0

![Grade and feedback](Оценка+отзыв.png)

## 🚀 How to view

1. **Report:** open `report.html` in your browser
2. **Code:** click the *Show/hide code* button in the top right corner of the report
3. **Dashboard:** requires RStudio to run (does not work in static HTML). If the user has a ClickHouse account and runs the code from their account, the dashboard will work locally.

## 🛠 Tools

- R
- DBI, ClickHouseHTTP (database connection)
- ggplot2 (visualization)
- caret, pROC (modeling and metrics)
- shiny (interactive dashboard)

## 📌 Author

Dmitrii Podolin  
HSE University, "Predictive Modeling and Applied Analytics" course
