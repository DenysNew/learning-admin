# Learning Admin Lab

This repository is my personal hands-on lab focused on learning system administration, Linux, security, and infrastructure fundamentals.

The main goal of this project is to build practical skills, document my learning process, and create a structured technical portfolio demonstrating real-world system analysis, troubleshooting, and administration workflows.

This repository reflects my progression in understanding how operating systems work internally, how to analyze system behavior, and how to identify both normal and abnormal activity.

---

## Objectives

The primary objectives of this lab are:

- Develop practical Linux system administration skills
- Understand system processes, services, and internal operating system mechanisms
- Learn how to analyze system logs and detect abnormal or suspicious activity
- Gain hands-on experience working with SSH, cron jobs, and system configurations
- Build and manage a structured virtual lab environment
- Document technical knowledge and practical exercises in a structured format
- Create a professional technical portfolio for entry-level IT, system administration, and cybersecurity roles

---

## Lab Environment

This lab environment is built using virtual machines and includes:

- Ubuntu Server — system administration practice
- Kali Linux — security analysis and investigation exercises
- VirtualBox — virtualization and isolated environment management
- Windows host system

The lab simulates real-world infrastructure environments, allowing safe experimentation, system analysis, and troubleshooting without affecting production systems.

---

## Repository Structure

This repository is organized to reflect different technical domains and learning areas:

learning-admin/
│
├── 00-meta/
│   ├── glossary.md        # My terminology glossary
│   ├── opsec.md           # Security and privacy guidelines
│   ├── roadmap.md         # Learning roadmap
│   └── templates/         # Templates for notes, reports, and labs
│
├── 10-admin/              # System administration
│   ├── linux/
│   ├── windows/
│   └── artifacts/
│
├── 20-pentest/            # Pentesting and security
│   ├── methodology.md     # My testing methodology
│   └── labs/
│
├── 30-architecture/       # System architecture and design
│   ├── diagrams/
│   └── notes/
│
└── 40-toolbox/            # Cheatsheets, commands, and tools

Each directory contains documentation, notes, commands, and artifacts related to specific technical topics.

---

## Topics Covered

This repository includes practical work and documentation related to:

- Linux system administration fundamentals
- Process monitoring and system behavior analysis
- System log analysis and interpretation
- SSH configuration and remote access concepts
- Cron jobs and task scheduling mechanisms
- System troubleshooting methodology
- Basic cybersecurity and persistence concepts
- Virtual lab setup and environment management

---

## Methodology

This lab follows a structured and practical learning approach.

Each topic typically includes:

- technical notes and explanations
- command usage and reference examples
- system artifacts such as logs, screenshots, and configurations
- observations and conclusions based on practical exercises

This methodology ensures both technical understanding and real hands-on experience.

---

## Purpose of this Repository

This repository serves as:

- a personal Linux administration and system analysis lab
- a structured technical knowledge base
- a portfolio demonstrating hands-on system administration and security skills
- a documented progression of technical learning and practical experience

The focus is on building real-world skills relevant to entry-level IT roles such as:

- Junior System Administrator
- IT Support Specialist
- SOC Analyst
- Infrastructure Support roles

---

## Skills Demonstrated

Through this lab, I have gained practical experience with:

### Linux Administration

- Navigating and understanding the Linux file system
- Managing users and permissions
- Working with system services and processes
- Understanding system startup and configuration mechanisms

### System and Process Analysis

- Identifying running processes using tools such as `ps aux`
- Analyzing process behavior and system activity
- Understanding process hierarchy and execution flow

### Log Analysis

- Reading and analyzing system logs (`/var/log/auth.log`, `syslog`)
- Identifying suspicious or abnormal system activity
- Understanding authentication and system events

### Networking Fundamentals

- Understanding TCP/IP basics
- Working with SSH connections
- Identifying active network connections using `ss` and `netstat`

### Persistence and Security Concepts

- Understanding persistence mechanisms such as cron jobs and shell configuration files
- Identifying suspicious system behavior and unauthorized access methods
- Applying basic incident analysis methodology

### Virtualization and Lab Environment

- Creating and managing virtual machines using VirtualBox
- Setting up isolated lab environments
- Practicing system administration in a controlled environment

### Documentation and Technical Workflow

- Structuring technical documentation
- Recording commands, observations, and system artifacts
- Maintaining a structured technical repository using Git and GitHub

---

## Author

Denys Nevskyi  
Aspiring IT Specialist focused on Linux, system administration, and cybersecurity.

# **Learning-Admin — Admin • Security • Pentest**

Этот репозиторий — мой персональный журнал обучения и практики в области системного администрирования, безопасности и пентестинга.
Это не просто конспекты, а структурированный набор знаний, лабораторных работ и артефактов, отражающих мой путь от понимания систем к их защите и тестированию.

---

## 🎯 Цели репозитория

1. **Развить фундамент администрирования** (Linux + Windows).
2. **Понять, как системы строятся, взаимодействуют и ломаются.**
3. **Освоить мышление пентестера, а не только инструменты.**
4. Создать **портфолио знаний и практики**, которое можно показать работодателю.
5. Научиться:

   * структурировать информацию,
   * документировать работу,
   * мыслить системно (сервисы, доверие, границы, риски).

---

## 🧠 Подход к обучению

Я придерживаюсь принципа:

**70% — практика (лабы, эксперименты, реальные системы)**
**30% — теория (документация, статьи, книги, разборы).**

Каждая тема должна оставлять после себя **артефакты**.

---

## 📁 Структура репозитория

```
learning-admin/
│
├── 00-meta/
│   ├── glossary.md        # Мой словарь терминов
│   ├── opsec.md           # Правила безопасности и приватности
│   ├── roadmap.md         # Дорожная карта обучения
│   └── templates/         # Шаблоны заметок, отчётов и лаб
│
├── 10-admin/              # Системное администрирование
│   ├── linux/
│   ├── windows/
│   └── artifacts/
│
├── 20-pentest/            # Пентест и безопасность
│   ├── methodology.md     # Мой подход к тестированию
│   └── labs/
│
├── 30-architecture/       # Системное мышление и архитектура
│   ├── diagrams/
│   └── notes/
│
└── 40-toolbox/            # Шпаргалки, команды, инструменты
```

---

## 📝 Правило артефактов (важно)

Для **каждой темы / лаб работы** я создаю:

1. **Заметку (.md)** с:

   * что изучал,
   * что делал,
   * что понял,
   * какие ошибки допустил.

2. Папку **`artifacts/`**, где лежат:

   * логи,
   * скриншоты,
   * конфиги,
   * команды,
   * диаграммы.

3. В конце каждой заметки обязательно:

   * ✅ **Что я понял**
   * 🔁 **Что нужно повторить / улучшить**

---

## 🔐 OPSEC (безопасность и приватность)

Я соблюдаю следующие правила:

* Не публикую реальные IP, пароли, токены, ключи.
* Замазываю чувствительные данные на скриншотах.
* Разделяю публичные и приватные материалы.
* Не раскрываю детали реальных систем и клиентов.

---

## 📚 Темы, которые я изучаю

### 🔹 Администрирование

* Linux:

  * пользователи и группы
  * права доступа (chmod, ACL)
  * systemd и логи
  * сети, сервисы, процессы

* Windows:

  * локальные пользователи и GPO
  * службы и журналы
  * основы Active Directory

### 🔹 Безопасность и пентест

* Разведка (OSINT + активная)
* Сканирование (Nmap, веб-разведка)
* Веб-безопасность (HTTP, запросы, файлы, логика)
* Базовые уязвимости (логика, доступы, конфигурации)

### 🔹 Системное мышление

* Как сервисы связаны между собой
* Где границы доверия
* Какие риски у системы
* Как атакующий может двигаться внутри сети

---

## 🚀 Как использовать этот репозиторий

Если ты:

* студент — можешь брать структуру как пример;
* начинающий админ — смотри раздел `10-admin`;
* начинающий пентестер — смотри `20-pentest`;
* работодатель — здесь виден мой реальный процесс обучения.

---

## 📬 Контакт / обратная связь

Если у тебя есть идеи, замечания или советы — буду рад фидбеку через Issues или Pull Requests.

---

**Статус репозитория:** активно пополняется и развивается.
**Автор:** Denys
**Последнее обновление:** регулярно.
