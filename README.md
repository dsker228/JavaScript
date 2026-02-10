def create_mermaid_flowchart():
    """Создает код для Mermaid.js блок-схемы"""
    mermaid_code = """
```mermaid
graph TD
    Start[Старт работы нейрона] --> InputData[Ввод входных параметров]
    
    InputData --> Normalize[Нормализация данных]
    Normalize --> WeightedSum[Вычисление взвешенной суммы]
    WeightedSum --> Activation[Применение функции активации]
    Activation --> Output[Вывод результата]
    Output --> End[Конец]
    
    subgraph "Детализация блока 'Ввод входных параметров'"
        A1[x1: доля подозрительных слов 0-1]
        A2[x2: наличие опасных вложений 0/1]
        A3[x3: количество внешних ссылок]
    end
    
    subgraph "Детализация блока 'Вычисление взвешенной суммы'"
        B1[z = w₁·x₁ + w₂·x₂ + w₃·x₃ + b]
        B2[где w - веса, b - смещение]
    end
    
    subgraph "Детализация блока 'Функция активации'"
        C1{Пороговая функция}
        C1 -->|z ≥ 0| C2[y = 1]
        C1 -->|z < 0| C3[y = 0]
    end
    
    subgraph "Детализация блока 'Вывод результата'"
        D1[y = 0] --> D2[Безопасное письмо]
        D3[y = 1] --> D4[Фишинговое письмо]
    end
    
    StartTraining[Начало обучения] --> Init[Инициализация весов]
    Init --> EpochLoop[Цикл по эпохам]
    EpochLoop --> ResetError[Обнуление ошибки]
    ResetError --> SampleLoop[Цикл по обучающим примерам]
    
    SampleLoop --> Predict[Предсказание ŷ]
    Predict --> CalculateError[Вычисление ошибки e = y - ŷ]
    CalculateError --> UpdateWeights[Обновление весов]
    UpdateWeights --> NextSample[Следующий пример]
    NextSample --> SampleLoop
    
    SampleLoop -->|Все примеры обработаны| EpochError[Расчет ошибки эпохи]
    EpochError --> CheckEpoch{Достигнут лимит эпох?}
    CheckEpoch -->|Нет| NextEpoch[Следующая эпоха]
    NextEpoch --> EpochLoop
    CheckEpoch -->|Да| EndTraining[Конец обучения]
    
    style Start fill:#e1f5fe
    style End fill:#f1f8e9
    style StartTraining fill:#fff3e0
    style EndTraining fill:#f3e5f5
