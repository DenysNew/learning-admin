# Microsoft 365 User Management and Licensing (Hybrid Identity)

## Overview (EN)

This lab demonstrates hybrid identity with on-premises Active Directory and Microsoft Entra ID. It covers user synchronization, user attribute updates from AD to cloud, license assignment, and access control based on enabled or disabled Microsoft Teams service.

---

## Описание (RU)

В данном сценарии реализована гибридная идентификация: пользователи создаются в локальной Active Directory, затем синхронизируются в Microsoft Entra ID и становятся доступны для управления в Microsoft 365. Далее показано изменение пользователя в AD, синхронизация изменений в облако, назначение лицензий и контроль доступа к Microsoft Teams.

---

# 1. Users synchronization (AD → Entra ID)

В этом разделе показано, что пользователи сначала существуют в локальной Active Directory, затем синхронизируются в Microsoft Entra ID и отображаются в Microsoft 365 Admin Center.

![AD Users](./artifacts/01-ad-users.png)

![Entra Users Sync](./artifacts/02-entra-users-sync.png)


![M365 Users](./artifacts/03-m365-active-users.png)

---

# 2. Change in AD → Sync to Cloud

В этом разделе показано, что изменение пользователя выполняется в Active Directory, затем запускается синхронизация, после чего обновление появляется в Entra ID. Это подтверждает, что источником управления для гибридного пользователя остается локальная AD.

![User Modification AD](./artifacts/04-ad-user-modification.png)

![Sync Command](./artifacts/05-ad-sync-command.png)

![User Updated Entra](./artifacts/06-entra-user-updated.png)

---

# 3. Cloud restriction (read-only)

В этом разделе показано, что после синхронизации гибридный пользователь виден в Entra ID, но его основные атрибуты нельзя свободно редактировать в облаке, потому что управление выполняется из локальной Active Directory.

![User Readonly](./artifacts/07-entra-user-readonly.png)

---

# 4. License assignment

В этом разделе показано назначение лицензии пользователю и итоговое состояние лицензирования в Microsoft 365 Admin Center.

![License Assigned](./artifacts/08-license-assigned.png)

![License Overview](./artifacts/09-license-overview.png)
---

# 5. Access control (Teams)

## Access allowed

В этом разделе показано, что пользователь с назначенной лицензией и доступным сервисом Teams может успешно войти в Microsoft Teams.

![Teams Allowed](./artifacts/10-teams-access-allowed.png)

## Teams disabled

В этом разделе показано, что лицензия у пользователя остается назначенной, но сервис Microsoft Teams внутри лицензии отключен вручную.

![Teams Disabled](./artifacts/11-teams-disabled-in-license.png)

## Access denied

В этом разделе показано, что пользователь не может получить доступ к Microsoft Teams, если сам сервис Teams отключен внутри назначенной лицензии.

![Teams Denied](./artifacts/12-teams-access-denied.png)

---

# 6. Groups (Cloud)

В этом разделе показано создание облачной группы в Microsoft Entra ID и добавление пользователя в состав группы.

![Groups Overview](./artifacts/01-groups-overview.png)

![Group Members](./artifacts/02-group-members.png)

---

# Conclusion

В лабораторной работе реализовано:

* создание пользователей в локальной Active Directory
* синхронизация пользователей в Microsoft Entra ID
* подтверждение того, что AD остается источником управления для гибридных пользователей
* назначение лицензий Microsoft 365
* проверка доступа к Teams при включенном сервисе
* проверка отказа в доступе при отключенном сервисе Teams
* создание и использование облачной группы в Entra ID

---

# Artifacts

Полная папка со всеми артефактами: [`artifacts`](./artifacts)
