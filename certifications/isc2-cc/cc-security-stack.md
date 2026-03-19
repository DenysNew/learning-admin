# CC Security Stack Overview (ISC2 CC)

## 📌 Overview (EN)
This document summarizes key security technologies for the ISC2 CC exam.
Focus: understanding roles, differences, and keywords.

---

## 🧠 Общая логика

Инструменты безопасности работают на разных уровнях:

- Endpoint (пользовательская машина)
- Network (сеть)
- Centralized analysis (централизованный анализ)

---

## 🔐 Firewall

 
Файрвол — это инструмент, который **разрешает или запрещает сетевой трафик** на основе заданных правил.

**Главная задача:**
- Контроль доступа (allow / deny)

**Keywords:**
- allow / deny  
- rules  
- ports  
- filtering  

---

## 🕵️ IDS (Intrusion Detection System)

 
IDS — система, которая **обнаруживает подозрительную активность**, но **ничего не блокирует**.

**Главная задача:**
- Мониторинг и уведомление (alert)

**Keywords:**
- detect  
- alert  
- monitor  

---

## 🛑 IPS (Intrusion Prevention System)

 Detects and blocks malicious activity.
  
IPS — система, которая **обнаруживает и сразу блокирует атаку**.

**Главная задача:**
- Активная защита (block)

**Keywords:**
- prevent  
- block  
- stop attack  

---

## 🖥️ EDR (Endpoint Detection and Response)

Monitors endpoint activity and responds to threats.

EDR — это агент, установленный на компьютере пользователя, который:
- собирает логи (процессы, входы, сеть)
- анализирует поведение
- может реагировать (например, изолировать машину)

**Главная задача:**
- Контроль и защита endpoint

**Keywords:**
- endpoint  
- behavior  
- response  

---

## 📊 SIEM (Security Information and Event Management)

 Centralized log collection and analysis.
 
SIEM — это центральная система, которая:
- собирает логи со всех систем
- анализирует их
- ищет подозрительные события

**Главная задача:**
- Централизованный анализ

**Keywords:**
- centralized  
- logs  
- correlation  
- events  

---

## 🤖 SOAR (Security Orchestration, Automation, and Response)

Automates incident response.

SOAR — система, которая **автоматизирует реагирование на инциденты**.

Пример:
- пришёл алерт → автоматически заблокировали IP

**Главная задача:**
- Автоматизация действий

**Keywords:**
- automation  
- playbooks  
- response  

---

## 🔑 Threat Intelligence

Provides information about known threats.
  
Threat Intelligence — это информация об угрозах:
- вредоносные IP
- домены
- сигнатуры атак

**Главная задача:**
- Помогает обнаруживать угрозы

**Keywords:**
- IOC  
- threat feeds  
- known threats  

---

## 🛡️ DLP (Data Loss Prevention)

Prevents data leakage.
 
DLP — система, которая **предотвращает утечку данных**.

Пример:
- блокирует отправку конфиденциальных файлов

**Главная задача:**
- Защита данных

**Keywords:**
- data leakage  
- sensitive data  
- exfiltration  

---

## 🧬 UEBA (User and Entity Behavior Analytics)

Detects abnormal behavior.

UEBA — система, которая анализирует поведение пользователей и ищет аномалии.

Пример:
- пользователь зашёл ночью с другой страны

**Главная задача:**
- Обнаружение подозрительного поведения

**Keywords:**
- behavior  
- anomaly  
- user activity  

---

## ⚔️ Различия (ВАЖНО ДЛЯ ЭКЗАМЕНА)

| Тип вопроса | Ответ |
|------------|------|
| allow / deny | Firewall |
| detect only | IDS |
| detect + block | IPS |
| endpoint monitoring | EDR |
| logs / correlation | SIEM |
| automation | SOAR |
| user behavior | UEBA |
| data leakage | DLP |
| IOC / threats | Threat Intelligence |

---

## 🧠 Экзаменационный алгоритм

1. Найди ключевые слова  
2. Определи уровень:
   - endpoint → EDR  
   - network → Firewall / IDS / IPS  
   - centralized → SIEM  

3. Определи действие:
   - detect → IDS  
   - block → IPS  
   - analyze → SIEM  

---

## 💡 Ключевая мысль

> Firewall = контроль  
> IDS = обнаружение  
> IPS = защита  
> EDR = контроль на машине  
> SIEM = центральный анализ  

---