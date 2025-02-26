### Звіт до лабораторної роботи: "Пошук та підготовка даних із обраного джерела"

### Підготувала студентка ТТП-42 Малашкіна Яна

#### 1. **Опис домену**

Ця лабораторна робота присвячена аналізу фінансових транзакцій. Основна мета — обробка даних про банківські операції та їх подальший аналіз за допомогою багатовимірного моделювання. Дані містять інформацію про банківські рахунки, карткові операції, клієнтів, кредити та інші фінансові аспекти.

#### 2. **Оригінальне джерело даних**

- **Посилання на набір даних**: [1999 Czech Financial Dataset](https://www.kaggle.com/datasets/mariammariamr/1999-czech-financial-dataset)
- **Опис набору даних**: Набір містить файли CSV, що представляють різні аспекти банківських операцій у Чехії. Основні таблиці:
  - `account.csv` — інформація про банківські рахунки.
  - `card.csv` — дані про банківські картки.
  - `client.csv` — персональні дані клієнтів.
  - `disp.csv` — відношення між власниками та рахунками.
  - `district.csv` — географічні дані клієнтів.
  - `loan.csv` — дані про кредити.
  - `order.csv` — замовлення клієнтів.
  - `trans.csv` — історія транзакцій.

#### 3. **Зіркова схема для OLAP сховища**

Була розроблена багатовимірна модель з двома таблицями фактів та 5-ма вимірами:

- **Факти (Fact 1 Table)**: `fact_trans`

  - Поля: `trans_id`, `account_id`, `date`, `client_id`, `district_id`, `card_id`, `amount`
 
  **Факти (Fact 2 Table)**: `fact_loan`

  - Поля: `loan_id`, `account_id`, `date`, `client_id`, `district_id`, `card_id`, `amount`

- **Вимірювання (Dimensions)**:
  - `Date Dimension (dim_date)`: рік, місяць, день, час.
  - `Account Dimension (dim_account)`: дані про рахунки.
  - `Client Dimension (dim_client)`: персональні дані.
  - `Card Dimension (dim_card)`: тип банківської картки.
  - `District Dimension (dim_district)`: географічні дані.

#### 4. **Опис ETL процесу**

Процес ETL (Extract, Transform, Load) реалізовано через Python. Основні файли в репозиторії:

- `csv_dataset.py` — обробка вихідних CSV-файлів.
- `bi_dataset.py` — трансформація даних у формат, зручний для аналізу.
- `html_page.py` — візуалізація даних.
- `dashboard.py` — головний контролер процесу.

Ключові кроки:

- Витягнення даних з CSV-файлів.
- Flattening ієрархії схеми сніжинки до схеми зірки шляхом денормалізації.
- Формування таблиць вимірів і фактів.

#### 5. **Опис Pivot Table**

Для аналізу даних було створено зведені таблиці:

1. Аналіз загальних сум транзакцій по роках та регіонах.
2. Аналіз загальних сум транзакцій по роках та типах карт.
3. Аналіз загальних сум кредитів по роках і районах.

#### 6. **Висновки**

У ході роботи були знайдені, оброблені та структуровані дані і також реалізовані візуалізації та створені pivot таблиці. Це дозволяє виконувати глибокий аналіз банківських транзакцій та кредитів і використовувати дані для бізнес-аналітики.
