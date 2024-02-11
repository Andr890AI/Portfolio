
- ПРОЕКТ:
Построение ML-продукта для оптимизации классификации заявок на оплату для сервиса Repetit.ru
- Описание проекта
Сервис Repetit.ru работает с большим количеством заявок от клиентов с данными о предмете, желаемой стоимости, возрасте ученика, целью занятий и тд. К сожалению, 7 из 8 не доходят до оплаты, при этом обработка заявки консультантом увеличивает конверсию в оплату на 30%.
Проблема в том, что консультантов не хватает на все заявки и получается, что чем больше заявок — тем меньше конверсия из заявки в оплату и консультанты тратят время на бесперспективные заявки.
- Задачи:
Разработать модель, которая по имеющейся информации о клиенте и заявке будет предсказывать вероятность оплаты заявки клиентом.
Заказчик хочет понять, какие заявки будут оплачены, а какие нет, чтобы одни обрабатывать вручную консультантами, а другие нет.
Оценка качества модели будет производиться с использованием precision и ROC-AUC.
Описание данных
Заявки (orders.feather)
order_date - дата создания
subject_id - предмет
purpose - цель занятий
lesson_price - цена
lesson_duration - желаемая проодолжительность урока
home_metro_id - ближайшее метро
add_info - доп инфо
start_date - начальная дата
working_teacher_id - работающий учитель
status_id - оплачена ли заявка (значения 6 и 13 говорят о факте оплаты заявки)
comments - комментарии
amount_to_pay - сумма к оплате
planned_lesson_number - клиент планирует N занятий
first_lesson_date - дата 1 занятия
coef - коэффициент
creator_id - кто создал заявку (id сотрудника или клиента)
pupil_category_new_id - возраст ученика
lessons_per_week - занятий а неделю
minimal_price - минимальная цена
teacher_sex - пол репетитора
teacher_experience_from - опыт репетитора от
teacher_experience_to- опыт репетитора до
lesson_place_new - онлайн, у ученика, у учителя
pupil_knowledgelvl -уровень знаний ученика
teacher_age_from - желаемый возраст репеитора от
teacher_age_to - желаемый возраст репеитора до
chosen_teachers_only - не предлагать репетиторов кроме выбранных самостоятельно
no_teachers_available - на заявку нет подходящих репов
source_id - где создана заявка (какая часть сайта, не регион)
original_order_id - дублем какой заявки является эта заявка
client_id - айди клиента
additional_status_id - дополнительный статус
max_metro_distance - максимально готов ехать от метро
estimated_fee - предполагая оплата
payment_date - дата платежа
test_group - аб тесты
is_display_to_teachers - хочет ли клиент получать отклики репетиторов
Репетиторы (teacher_info.feather)
date_update - дата обновления
reg_date - дата регистрации
birth_date - дата рождения
teaching_start_date - дата начала обучения
user_id - айди
is_email_confirmed -подтвержденная почта
is_home_lessons - домашние уроки
is_external_lessons - внешние уроки
external_comments - внешние комментарии
lesson_duration - продолжит урока
lesson_cost - стоимость урока
status_id - статус
status_relevant_date - дата статусу
status_school_id - статус школы
status_college_id - статус колледжа
status_display - отображение состояния
russian_level_id - российский уровень
home_country_id - родная страна
education - образование
information - информация
is_confirmed - подтвержденный
is_display - показывается в каталоге
rating_id - id рейтинга
rating - рейтинг
comments - комментарии
rules_confirmed_date - дата подтверждения
last_visited - послеждний визит
is_pupils_needed - открыт для заявок
is_cell_phone_confirmed - сотовый телефон
effective_rating - какой-то еще рейтинг
area_id - область
registrar_id - регистратор
pupil_needed_date - нужная дата
sex - пол
amount_to_pay - долг
is_remote_lessons - удаленные уроки
remote_comments - удаленные комментарии
show_on_map - показать на карте
send_mailing - почтовая рассылка
send_suitable_orders - подходящие заказы
rating_for_users - рейтинг 2
rating_for_admin - рейтинг 3
passport_id - пароль
is_edited -= отредактированный
orders_allowed - разрешено назначать на заявки
display_days - дни показа
verification_status_id - статус проверки
is_individual - индивидуальный
partner_id - партнер
tar_rating - рейтинг 4
rating_for_users_yesterday - рейтинг вчера
review_num - отзывы
relevance_date - актуальные дата
is_display_at_partners - демонстрация у партнеров
video_presentation_id - есть видеопрезентация
status_institution_id - статус учреждения
Free_time_relevance_date - Свободное время актуальная дата
Подходящие по фильтру репетиторы (suitable_teachers.feather)
tteacher_id - id репетитора
order_id - id заявки
contact_result - результат контакта
enable_auto_assign - доступен ли репетитор к работе или заблокирован (может ли репетитора назначить консультант и может ли он сам назначиться) (значение известно на момент подачи заявки)
enable_assign - доступен ли репетитор к работе или заблокирован (может ли репетитора назначить консультант и может ли он сам назначиться) (значение известно на момент подачи заявки)
Желаемые репетиторы (prefered_teachers_order_id.feather) Репетиторы, которых клиент выбрал клиент.
tteacher_id - id репетитора
order_id - id заявки
План реализации:
загрузка и ознакомление с данными,
предварительная обработка и отбор полезных признаков,
полноценный разведочный анализ,
разработка новых синтетических признаков,
отбор финального набора обучающих признаков.
выбор и обучение моделей,
итоговая оценка качества предсказания лучшей модели,
анализ важности ее признаков.
