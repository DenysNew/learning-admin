# Blue Team / SOC Track

This section documents my practical training in Security Operations (SOC) and Blue Team activities.  
The hands-on exercises are primarily based on labs from TryHackMe, combined with independent analysis and structured documentation aligned with junior SOC analyst responsibilities.

---

# 🔵 20-blue-team

Этот раздел посвящён практическому изучению работы аналитика SOC (Security Operations Center).

Практическая часть основана преимущественно на лабораториях платформы TryHackMe, 
где я отрабатываю навыки анализа логов, расследования алертов и навигации в SIEM-инструментах.

Цель — не просто пройти комнаты, а выстроить системное понимание:

- как ориентироваться в SIEM и EDR,
- как анализировать основные типы алертов,
- как действовать по алгоритму (playbook),
- как принимать решения и классифицировать инциденты.

---

## 📁 Структура раздела

### 10-siem-interface

Изучение интерфейсов и навигации:

- где искать алерты
- как пользоваться поиском
- как фильтровать события
- как анализировать timeline
- как работать с данными хоста

Фокус: уверенность в инструменте.

---

### 20-core-alerts

Базовые типы алертов, которые чаще всего встречаются в работе Junior SOC:

- Brute Force
- Phishing
- Suspicious PowerShell
- Malware (hash-based detection)
- Suspicious outbound traffic

Фокус: распознавание паттернов атак.

---

### 30-playbooks

Пошаговые алгоритмы реагирования:

- что проверять первым
- какие IOC анализировать
- как классифицировать инцидент
- когда эскалировать

Фокус: формирование operational мышления.

---

### artifacts

Скриншоты, логи и дополнительные материалы, полученные в ходе практики.

---

## 🎯 Общая цель

Сформировать уровень Junior SOC Analyst, который:

- не теряется в интерфейсе SIEM,
- понимает структуру инцидента,
- умеет анализировать IOC,
- способен классифицировать алерт,
- знает базовый workflow расследования.

Этот раздел отражает практический прогресс в Blue Team направлении с использованием TryHackMe как основной лабораторной платформы.