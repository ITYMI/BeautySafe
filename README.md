# <a name="Start"> BeautySafe</a>

## Состав команды:
- Галкина Валерия - ИВТ-22-22
- Григорьева Ксения - ИВТ-22-22

##
- [BeautySafe](#Start)
   - [Постановка задачи](#Task)
      - [Модель угроз](#Threats)
      - [Модель нарушителя](#Intruder)
   - [Архитектура (до кибериммунизации)](#Architecture1)
      - [Негативные сценарии](#NegativeScenarios)
      - [Позитивные сценарии](#PositiveScenarios)
   - [Архитектура (после кибериммунизации)](#Architecture2)
      - [Решение](#Decision)
   - [Использованная литература](#Sources)

## <a name="Task"> Постановка задачи</a>
Разработать и внедрить онлайн-платформу "BeautySafe", обеспечивающую безопасное бронирование и оплату услуг в сфере красоты, с максимальной защитой персональных данных пользователей и безопасностью финансовых операций.

## <a name="Threats">Модель угроз</a>
| Категория угроз | Потенциальная угроза | Уровень риска |
| --------------- | ----------- | ----------- |
| **Нарушение конфиденциальности** | Несанкционированный доступ к персональным данным и платежной информации | Высокий |
|                                     | Перехват данных при передаче по сетям связи | Высокий |
| **Нарушение целостности данных** | Изменение данных без санкционирования  | Средний |
|                                     | Внедрение вредоносного кода | Средний |
| **Нарушение доступности данных**    | DDoS-атаки  | Высокий |
|                                     | Отказ оборудования или ПО | Средний |
| **Ошибки в ПО**                     | Уязвимости в веб-приложении и мобильных приложениях | Высокий |
|                                     | Ошибки конфигурации серверов и баз данных | Средний |


## <a name="Intruder">Модель нарушителя</a>

| **Тип нарушителя**        | **Описание**                                      | **Цель**                                                      | **Угрозы**                                                                                     | **Меры защиты**                                                                                                                                                       |
|---------------------------|---------------------------------------------------|---------------------------------------------------------------|------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Внешние нарушители**| Киберпреступники, хакеры, организованные группы   | Кража данных, финансовые мошенничества, выведение системы из строя | - Несанкционированный доступ к системе<br>- Кража персональных данных и финансовой информации<br>- DDoS атаки<br>- Эксплуатация уязвимостей в ПО | - Двухфакторная аутентификация <br>- Шифрование данных <br>- Ограничение доступа на основе ролей и привилегий <br>- Облачная защита от DDoS <br>- Регулярные обновления  |
| **Внутренние нарушители** | Недобросовестные сотрудники, контракторы         | Кража данных, саботаж, передача корпоративной информации конкурентам | - Несанкционированный доступ к конфиденциальной информации<br>- Изменение или уничтожение данных<br>- Саботаж работы системы<br>- Передача корпоративной информации конкурентам | - Ограничение прав доступа <br>- Мониторинг и журналирование действий сотрудников<br>- Проведение аудитов безопасности<br>- Обучение сотрудников политикам безопасности |
| **Конкуренты**     (как отдельно выделенный подклас внешних нарушителей)       | Компании-конкуренты, промышленный шпионаж         | Кража коммерческой информации, дискредитация компании          | - Кража коммерческой информации<br>- Дискредитация компании<br>- Эксплуатация уязвимостей для получения конкурентного преимущества | - Шифрование данных<br>- Пентесты<br>- Обучение сотрудников<br>- Политика конфиденциальности и защита интеллектуальной собственности |


## <a name="Purposes">Цели и Предположения безопасности</a>
### Цели безопасности:  
1. Защита личной информации пользователей
2. Борьба с мошенничеством и фальсификацией
3. Защита от финансовых рисков  

### Предположения безопасности  
1. Безопасная инфраструктура:
- Система развернута на защищенной инфраструктуре с использованием современных средств защиты (например, облачные сервисы с поддержкой безопасности).
- Используются защищенные каналы связи для передачи данных (HTTPS, VPN).
2. Обученные пользователи:
- Пользователи и сотрудники понимают основы безопасности и следуют рекомендациям по безопасности (например, не разглашают пароли, используют 2FA).
3. Регулярные обновления:
- Программное обеспечение и системы безопасности регулярно обновляются для защиты от новых уязвимостей.
4. Контроль доступа:
- Доступ к критическим системам и данным ограничен и контролируется на основе принципов минимальных привилегий.
5. Мониторинг и реагирование на инциденты:
- В системе реализованы механизмы мониторинга и обнаружения угроз, а также процедуры реагирования на инциденты безопасности.

- ## <a name="Architecture1"> Архитектура (до кибериммунизации)</a>

### Общая структура системы
![Архитектура системы до кибериммунизации](https://github.com/ITYMI/BeautySafe/blob/main/%D1%81%D1%85%D0%B5%D0%BC%D0%B0%20%D0%B0%D1%80%D1%85%D0%B8%D1%82%D0%B5%D0%BA%D1%82%D1%83%D1%80%D1%8B%20%D0%B4%D0%BE%20%D0%BA%D0%B8%D0%B1%D0%B5%D1%80%D0%B8%D0%BC%D0%BC%D1%83%D0%BD%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8.JPG)
- Клиентское приложение (веб и мобильное)
- Серверное приложение (API)
- База данных
- Платежный шлюз

### Угрозы в архитектуре до кибериммунизации
- Отсутствие шифрования данных при передаче.
- Недостаток аутентификации и авторизации.
- Уязвимости в сторонних компонентах.

## <a name="NegativeScenarios"> Негативные сценарии</a>
![Негативные сценарии](https://github.com/ITYMI/BeautySafe/blob/main/%D1%81%D1%85%D0%B5%D0%BC%D0%B0%20%D0%BD%D0%B5%D0%B3%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D1%8B%D1%85%20%D1%81%D1%86%D0%B5%D0%BD%D0%B0%D1%80%D0%B8%D0%B5%D0%B2.JPG)
1. **Несанкционированный доступ к учетной записи пользователя**:
   - Описание: Атакующий использует украденные учетные данные для доступа к учетной записи.
   - Последствия: Утечка личной информации, финансовые потери.

2. **Перехват данных при передаче**:
   - Описание: Атакующий использует атаки типа "человек посередине" для перехвата данных.
   - Последствия: Утечка конфиденциальной информации.

3. **Атака на платежный шлюз**:
   - Описание: Атакующий использует уязвимость в платежном шлюзе для кражи данных о платежах.
   - Последствия: Финансовые потери для пользователей и компании.

## <a name="Architecture2"> Архитектура (после кибериммунизации)</a>
![Архитектура после кибериммунизации](https://github.com/ITYMI/BeautySafe/blob/main/%D1%81%D1%85%D0%B5%D0%BC%D0%B0%20%D0%B0%D1%80%D1%85%D0%B8%D1%82%D0%B5%D0%BA%D1%82%D1%83%D1%80%D1%8B%20%D0%BF%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BA%D0%B8%D0%B1%D0%B5%D1%80%D0%B8%D0%BC%D0%BC%D1%83%D0%BD%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8.JPG)
### Изменения в архитектуре
- Внедрение шифрования данных на всех уровнях.
- Реализация многофакторной аутентификации.
- Использование защищенных протоколов (например, HTTPS) для всех соединений.

### Позитивные сценарии
![Позитивные сценарии](https://github.com/ITYMI/BeautySafe/blob/main/%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%B8%D0%B2%D0%BD%D1%8B%D1%85%20%D1%81%D1%86%D0%B5%D0%BD%D0%B0%D1%80%D0%B8%D0%B5%D0%B2%20%D1%81%D1%85%D0%B5%D0%BC%D0%B0.JPG)
- **Сценарий 1**: Пользователь успешно проходит аутентификацию через многофакторную аутентификацию.
- **Сценарий 2**: Данные пользователей надежно шифруются и передаются через защищенные каналы.

## <a name="Decision"> Решение</a>
![Решение](https://github.com/ITYMI/BeautySafe/blob/main/%D1%81%D1%85%D0%B5%D0%BC%D0%B0%20%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D1%8F.JPG)
### Меры по предотвращению нарушений конфиденциальности
1. **Шифрование данных**:
   - Использование современных алгоритмов шифрования для хранения и передачи данных.

2. **Многофакторная аутентификация**:
   - Обеспечение дополнительного уровня защиты при входе в систему.

3. **Регулярные аудиты безопасности**:
   - Проведение проверок и тестов на проникновение для выявления уязвимостей.

4. **Обучение сотрудников и пользователей**:
   - Регулярные тренинги по безопасности для пользователей и сотрудников.

5. **Мониторинг системы**:
   - Внедрение систем мониторинга и реагирования на инциденты.

## <a name="Sources"> Использованная литература</a>
- БДУ ФСТЭК
- Федеральный закон от 29 июля 2018 г. № 250-ФЗ "О внесении изменений в Закон Российской Федерации "О защите прав потребителей"
- Федеральный закон от 28 декабря 2009 г. № 381-ФЗ "Об основах государственного регулирования торговой деятельности в Российской Федерации"
- Закон РФ от 7 февраля 1992 г. № 2300-I "О защите прав потребителей"

