# 🌸 PR9: Auth Feature (Clean Architecture + MVI)

Практическая работа №9 по дисциплине "Современные паттерны проектирования в Android". 
Проект демонстрирует реализацию модуля авторизации с использованием современных стандартов Android-разработки.

## 🎯 Особенности и соответствие критериям оценки
- ✅ **Unidirectional Data Flow (UDF):** Состояние экрана (UI State) является неизменяемым. Любое действие пользователя (Intent) приводит к обновлению состояния через ViewModel.
- ✅ **Реактивность:** Использование `StateFlow` и `viewModelScope` обеспечивает мгновенную реакцию UI на изменения (валидация полей, блокировка кнопки при загрузке).
- ✅ **Clean Architecture:** Строгое разделение на слои: Presentation, Domain и Data. Бизнес-логика (UseCase) не зависит от Android SDK.
- ✅ **Dependency Injection:** Полная настройка внедрения зависимостей через Hilt (KSP).
- ✅ **Error Handling:** Ошибки обрабатываются через обновление State и отображаются через `SnackbarHost` (Material 3), а не устаревшие Toast.
- ✅ **Тестируемость:** Domain-слой изолирован и готов к покрытию Unit-тестами (JUnit + MockK).

## 🛠 Технологический стек
- **Язык:** Kotlin 2.0.21
- **UI:** Jetpack Compose + Material 3 (Пастельно-розовая тема)
- **Архитектура:** Clean Architecture + MVVM/MVI
- **Асинхронность:** Kotlin Coroutines + Flow (StateFlow)
- **DI:** Dagger Hilt + KSP
- **Сборка:** Gradle (Kotlin DSL), JVM Target 17

## 📂 Структура проекта
```text
app/src/main/java/com/example/pr9/
├── di/                 # Модули Hilt (AppModule)
├── domain/             # Чистая бизнес-логика (не зависит от Android)
│   ├── model/          # Бизнес-сущности (User)
│   ├── repository/     # Контракты (интерфейсы)
│   └── usecase/        # Сценарии использования (AuthUseCase)
├── data/               # Источники данных
│   └── repository/     # Реализация контрактов (AuthRepositoryImpl)
└── presentation/       # UI-слой (MVI)
    ├── AuthUiState.kt  # Неизменяемое состояние экрана
    ├── AuthViewModel.kt# Обработчик логики и Intent'ов
    ├── LoginScreen.kt  # Экран авторизации (Compose)
    └── HomeScreen.kt   # Экран профиля после успешного входа