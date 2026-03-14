# Incident Response Lifecycle

## Short description
This note summarizes the Incident Response Lifecycle for ISC2 Certified in Cybersecurity (CC) preparation. It includes the main phases, key English terms, and exam-oriented patterns that help quickly understand test questions.

---

# Incident Response Lifecycle

## Что это такое

**Incident Response** — это процесс реагирования на инциденты информационной безопасности.

Главная цель Incident Response:

- **minimize the impact of security incidents**
- **reduce damage**
- **restore systems and operations**

То есть задача не в том, чтобы гарантированно предотвратить все атаки, а в том, чтобы:

1. обнаружить инцидент  
2. локализовать его  
3. удалить причину  
4. восстановить систему  
5. сделать выводы на будущее  

---

# Correct order of phases

Правильный порядок фаз жизненного цикла Incident Response:

1. **Preparation**
2. **Identification**
3. **Containment**
4. **Eradication**
5. **Recovery**
6. **Lessons Learned**

---

# Phase overview

## 1. Preparation
### Смысл
Подготовка к возможным инцидентам.

### Что сюда входит
- policies
- procedures
- playbooks
- tools
- roles and responsibilities
- communication plan
- logging and monitoring setup

### Ключевые английские слова
- **prepare**
- **before an attack**
- **policies**
- **procedures**
- **tools**
- **readiness**

### Экзаменационная логика
Если вопрос про подготовку до атаки, обычно это **Preparation**.

---

## 2. Identification
### Смысл
Обнаружение и подтверждение того, что инцидент действительно произошёл.

### Что сюда входит
- detecting suspicious activity
- confirming the incident
- initial analysis
- identifying affected systems

### Ключевые английские слова
- **identify**
- **detect**
- **discover**
- **confirm**
- **incident has occurred**
- **suspicious activity**

### Экзаменационная логика
Если в вопросе есть слова про обнаружение, подтверждение, замеченную угрозу, это обычно **Identification**.

---

## 3. Containment
### Смысл
Остановить распространение атаки и ограничить ущерб.

### Что сюда входит
- isolating compromised systems
- disabling accounts
- blocking malicious traffic
- segmenting affected network areas

### Ключевые английские слова
- **contain**
- **isolate**
- **stop the spread**
- **limit damage**
- **affected systems**
- **compromised systems**

### Экзаменационная логика
Если в вопросе есть:
- остановить распространение
- изолировать заражённую систему
- не дать атаке пойти дальше

это обычно **Containment**.

---

## 4. Eradication
### Смысл
Полностью удалить угрозу и устранить корневую причину атаки.

### Что сюда входит
- removing malware
- deleting malicious files
- closing vulnerabilities
- removing backdoors
- eliminating root cause

### Ключевые английские слова
- **remove**
- **eradicate**
- **eliminate**
- **root cause**
- **remove malware**
- **delete malicious code**

### Экзаменационная логика
Если вопрос про удаление malware или устранение причины атаки, это **Eradication**.

---

## 5. Recovery
### Смысл
Восстановление систем и возвращение работы к нормальному состоянию.

### Что сюда входит
- restoring systems
- validating system integrity
- returning services to production
- monitoring for recurrence

### Ключевые английские слова
- **recover**
- **restore**
- **return to normal**
- **resume operations**
- **after the threat has been removed**

### Экзаменационная логика
Если в вопросе есть слова про восстановление, возврат к нормальной работе, запуск сервисов после атаки — это **Recovery**.

---

## 6. Lessons Learned
### Смысл
Анализ произошедшего инцидента и улучшение защиты на будущее.

### Что сюда входит
- post-incident review
- documentation
- recommendations
- process improvement
- control improvement
- updating playbooks

### Ключевые английские слова
- **lessons learned**
- **review**
- **after-action review**
- **improve controls**
- **update procedures**
- **document findings**

### Экзаменационная логика
Если вопрос про анализ после инцидента, выводы, улучшение процессов и контроля — это **Lessons Learned**.

---

# Main goal of Incident Response

## Основная цель Incident Response Plan
**To minimize the impact of security incidents.**

Не:
- гарантированно предотвратить все атаки
- только писать политики
- только искать уязвимости

А именно:
- снизить ущерб
- быстро отреагировать
- восстановить работу

---

# Quick exam patterns

## Incident Response patterns

| English phrase | Meaning | Likely answer |
|---|---|---|
| detect the incident | обнаружить инцидент | Identification |
| confirm a security incident | подтвердить инцидент | Identification |
| isolate affected systems | изолировать затронутые системы | Containment |
| stop the attack from spreading | остановить распространение атаки | Containment |
| remove malware | удалить вредоносное ПО | Eradication |
| eliminate the root cause | устранить корневую причину | Eradication |
| restore systems | восстановить системы | Recovery |
| return operations to normal | вернуть работу к норме | Recovery |
| review the incident | разобрать инцидент | Lessons Learned |
| improve controls after the incident | улучшить меры защиты после инцидента | Lessons Learned |

---

# Important English vocabulary

## Core words

| English | Russian |
|---|---|
| incident | инцидент |
| response | реагирование |
| lifecycle | жизненный цикл |
| identify | выявить / определить |
| detect | обнаружить |
| confirm | подтвердить |
| contain | локализовать / сдержать |
| isolate | изолировать |
| affected system | затронутая система |
| compromised system | скомпрометированная система |
| eradicate | устранить полностью |
| root cause | корневая причина |
| recover | восстановить |
| restore | восстановить |
| lessons learned | извлечённые уроки |
| damage | ущерб |
| impact | влияние / последствия |
| spread | распространение |
| malware | вредоносное ПО |
| breach | нарушение безопасности / взлом |

---

# Easy memory formula

## Short chain

Preparation → Identification → Containment → Eradication → Recovery → Lessons Learned

## Very short meaning

Prepare → Detect → Isolate → Remove → Restore → Improve

---

# Typical exam traps

## 1. Containment vs Eradication

### Containment
Остановить распространение атаки.

### Eradication
Удалить саму угрозу из системы.

---

## 2. Recovery vs Lessons Learned

### Recovery
Восстановить систему и вернуть работу к норме.

### Lessons Learned
Разобрать инцидент и улучшить защиту на будущее.

---

## 3. Prevention vs Incident Response

Incident Response не гарантирует предотвращение всех атак.

Incident Response нужен, когда:
- атака уже произошла
- инцидент уже обнаружен
- нужно снизить ущерб и восстановиться

---

# Mini examples

## Example 1
Question idea:  
Which phase focuses on isolating compromised systems?

Answer:  
Containment

---

## Example 2
Question idea:  
Which phase focuses on removing malware and eliminating the root cause?

Answer:  
Eradication

---

## Example 3
Question idea:  
Which phase focuses on restoring normal operations?

Answer:  
Recovery

---

## Example 4
Question idea:  
Which phase includes reviewing the response and improving procedures?

Answer:  
Lessons Learned

---

# Final summary

Incident Response Lifecycle is one of the core security topics for ISC2 CC.

The most important points to remember:

Goal: minimize impact and reduce damage

Order:  
Preparation → Identification → Containment → Eradication → Recovery → Lessons Learned

Containment: stop spread  
Eradication: remove threat  
Recovery: restore systems  
Lessons Learned: improve after incident

---

# Key English exam words

detect  
confirm  
isolate  
stop spread  
remove malware  
root cause  
restore  
improve controls