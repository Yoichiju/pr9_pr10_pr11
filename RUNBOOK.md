# Runbook: PR9 Auth Project

Этот документ содержит инструкции по сборке, тестированию и устранению типичных неполадок в проекте.

## 📋 Предварительные требования
- **Android Studio:** Iguana, Jellyfish, Ladybug или новее.
- **JDK:** JetBrains Runtime (JBR) 17 (проверяется в `File -> Project Structure -> SDK Location`).
- **Gradle:** Версия wrapper 8.7.x или 8.9.x.

## 🛠 Команды сборки (через Terminal)
```bash
# Очистка предыдущих сборок (рекомендуется при странных ошибках)
./gradlew clean

# Полная пересборка проекта
./gradlew build

# Запуск Unit-тестов (для проверки Domain-слоя)
./gradlew test