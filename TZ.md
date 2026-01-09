Техническое задание: Сервис по оптимизации рациона и расчёта суточной нормы для домашних животных с учетом индивидуальных параметров и целей 
( PetDiet)
1. Цель проекта
Разработка веб-сервиса для расчета оптимального рациона домашних животных на основе ветеринарных формул. Сервис помогает владельцам контролировать вес питомцев, предотвращать ожирение и составлять сбалансированный рацион.

2. Роли пользователей
•	Гость:  Просмотр демо-расчетов, информации о формулах
•	Пользователь:  Регистрация, добавление питомцев, ведение дневника питания, просмотр аналитики

3. Модели данных
Pet (Питомец)
•	name, species (cat/dog), breed, weight, age, activity_level, reproductive_status, goal (lose/maintain/gain)
•	created_at, updated_at, owner (ForeignKey to User)

FoodProduct (Продукт)
•	name, brand, type (dry/wet/raw/treat)
•	calories_per_100g, protein_g, fat_g, carbs_g, fiber_g
•	is_approved (модерация)

FeedingRecord (Кормление)
•	pet (ForeignKey), food_product (ForeignKey), amount_g, feeding_time
•	calculated_calories, calculated_protein и т.д.

DailyReport (Дневной отчет)
•	pet (ForeignKey), date
•	total_calories, total_protein, total_fat, total_carbs
•	rer_value, der_value, protein_norm, fat_norm, carb_norm
•	weight_change_prediction (прогноз изменения веса)

4. Ключевой функционал
•	Регистрация и добавление питомца с указанием всех параметров
•	Расчет RER/DER и норм БЖУ по формулам при добавлении/изменении питомца
•	Ведение дневника питания с выбором продуктов из базы
•	Автоматический расчет съеденных калорий и нутриентов
•	Построение графиков динамики веса и сравнения фактического питания с нормами
•	Прогноз изменения веса на основе калорийного баланса

5. Внешние интеграции / Аналитика
•	Библиотеки:  Pandas для расчетов, Matplotlib/Plotly для визуализации
•	Формулы: Ветеринарные формулы RER/DER, расчет БЖУ в граммах
