# Learning Admin

Dokumentacja mojej praktyki w administracji IT: konfiguracje, rozwiązywanie problemów i zrzuty ekranu z wykonanych ćwiczeń. Główne środowisko to VirtualBox, Windows Server, Ubuntu oraz Microsoft 365.

**[Portfolio — projekty i CV](https://portfolio.appli-lab.pl/#admin)**

## Od czego zacząć

| Obszar | Co pokazuje dokumentacja | Przykład |
| --- | --- | --- |
| Windows Server i Active Directory | Kontroler domeny, OU, użytkownicy, grupy, RSAT, DNS i DHCP | [Naprawa DHCP po promocji serwera do DC](10-admin/windows/active-directory/dhcp-not-working-after-dc-promotion.md) |
| Microsoft 365, Entra ID i Intune | Synchronizacja tożsamości, licencje, MFA i dostęp zależny od zgodności urządzenia | [Trzy scenariusze Conditional Access](20-microsoft365/30-security/conditional-access-compliant-device/conditional-access-compliant-device.md) |
| Linux | Uprawnienia plików, właściciele i analiza plików SUID | [Praktyka z czterema zrzutami](10-admin/linux/linux-file-permissions.md) |
| Sieci i dostęp zdalny | Sieć lab-net, OpenVPN, certyfikaty, routing i NAT | [Dostęp przez VPN do sieci laboratoryjnej](30-vpn/30-network-access/network-access.md) |

## Dokumentacja według obszaru

### Windows Server i Active Directory

- [Wdrożenie kontrolera domeny](10-admin/windows/active-directory/domain-controller-deployment.md)
- [Osobna stacja administratora i RSAT](10-admin/windows/admin-workstation-setup.md)
- [OU, konta i grupy zarządzane ze stacji administratora](20-microsoft365/10-onprem-identity/ad_setup.md)
- [Diagnostyka DHCP i DNS po promocji do DC](10-admin/windows/active-directory/dhcp-not-working-after-dc-promotion.md)

### Microsoft 365, Entra ID i Intune

- [Synchronizacja AD z Entra ID](20-microsoft365/20-hybrid-identity/ad-connect-sync.md)
- [Użytkownicy, licencje i dostęp do usług](20-microsoft365/10-user-management/user-management.md)
- [Conditional Access i MFA](20-microsoft365/30-security/conditional-access-mfa/conditional-access-mfa.md)
- [Intune i dostęp z urządzeń zgodnych oraz niezarządzanych](20-microsoft365/30-security/conditional-access-compliant-device/conditional-access-compliant-device.md)

### Linux

- [Uprawnienia i SUID — wykonane ćwiczenie](10-admin/linux/linux-file-permissions.md)
- [Uprawnienia, SUID, SGID i sticky bit — krótka ściąga](10-admin/linux/file-permissions.md)

### Sieci i dostęp zdalny

- [Środowisko VirtualBox i plan sieci](10-admin/lab-virtualization/README.md)
- [Instalacja i konfiguracja serwera OpenVPN](30-vpn/10-openvpn-server-setup/openvpn-setup.md)
- [Profil klienta i połączenie VPN](30-vpn/20-openvpn-client/client-setup.md)
- [Routing, NAT i test dostępu do lab-net](30-vpn/30-network-access/network-access.md)

## Materiały uzupełniające

- [Odzyskanie dostępu do własnej maszyny Windows i wnioski o ochronie dysku](10-admin/windows/password-recovery-utilman-exploit.md)
- [Notatki Blue Team i playbooki](20-blue-team/README.md)
- [Notatki do ISC2 CC](certifications/isc2-cc/)
- [Git — używane polecenia](40-toolbox/commands/git.md)
- [Dalszy plan nauki](00-meta/roadmap.md) · [Słownik](00-meta/glossary.md) · [Zasady publikowania](00-meta/opsec.md)

## Jak czytać repozytorium

Nawigacja jest po polsku; większość szczegółowych zapisów pozostaje po rosyjsku, część zawiera angielski skrót. Zrzuty przedstawiają rzeczywiste etapy ćwiczeń. Prywatne adresy IP, nazwy VM i konta testowe opisują środowisko laboratoryjne.

Notatki teoretyczne i planowane tematy są oznaczone osobno. Sam opis procedury nie oznacza przeprowadzonego wdrożenia. Daty, wersje i wyniki w poszczególnych notatkach odnoszą się do momentu wykonania ćwiczenia.
