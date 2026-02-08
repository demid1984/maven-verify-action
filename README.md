# github-ci
Базовые инструменты для CI/CD

# Maven Verify Action

**Универсальный Composite GitHub Action для запуска Maven verify с динамическими переменными окружения.**

## 📋 Обзор

Этот Action предоставляет стандартизированный способ выполнения команды `mvn verify` в проектах Maven с поддержкой:
- Автоматической настройки Java
- Передачи файла `settings.xml`
- Активации профилей Maven
- Динамической установки переменных окружения для использования в `settings.xml`

## 🚀 Быстрый старт

### Базовый пример

```yaml
jobs:
  verify:
    runs-on: ubuntu-latest
    steps:
      - name: Run Maven Verify
        uses: demid1984/maven-verify-action@v1.0.0
        with:
          java-version: '21'
          distribution: 'temurin'
          m2-settings: '.m2/settings.xml'
          profile-name: 'github'
          maven-args: '-DskipTests'
          env-vars-multiline: |
            REPO_USERNAME=${{ secrets.MAVEN_USERNAME }}
            REPO_PASSWORD=${{ secrets.MAVEN_PASSWORD }}
            MAVEN_OPTS=-Xmx2g
            NEXUS_URL=https://nexus.company.com
            # Комментарий
            CUSTOM_SETTING=value