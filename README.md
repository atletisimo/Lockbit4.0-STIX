# Lockbit4.0-STIX
Краток опис на STIX моделот(LockBit 4.0 Ransomware Инцидент)

Scenario
Ова сценарио претставува координирана ransomware кампања насочена кон критичната инфраструктура во Албанија.

Целта е финансиска добивка преку брзо криптирање на фајлови и примена на техника на двојна изнуда (double extortion),.

Сценариото го илустрира целосното поврзување на објектите Identity, Threat Actor, Malware, Campaign, Attack Patterns и Indicators.
Data model
За структурирано претставување на сценариото е искористен STIX 2.1 (Structured Threat Information Expression) моделот. 
Моделот е имплементиран преку STIX Domain Objects (SDO) и Relationship Objects (SRO).
Identity SDO
Во моделот е дефиниран Identity објект кој ја претставува жртвата на нападот – Critical Infrastructure Organization – Albania.
Овој објект е моделиран со користење на  STIX Domain Objects (SDO’s), што овозможува формално идентификување на организацијата и нејзиниот сектор (critical-infrastructure).
Identity објектот се користи и како централна референтна точка во моделот бидејќи:
    • Threat Actor ја таргетира организацијата
    • Campaign исто така ја таргетира истата инфраструктура
Threat Actor SDO
Threat Actor објектот ги претставува LockBit ransomware operators, кои имаат:
    • Primary motivation: financial
    • Sophistication: advanced
    • Resource level: team
Во моделот постои релација:
Threat Actor → uses → Malware
Threat Actor → targets → Identity

што покажува дека напаѓачот го користи LockBit malware и ја таргетира критичната инфраструктура.
Malware SDO
Malware објектот го претставува LockBit 4.0 ransomware .
Во моделот постои релација:
Malware → uses → Attack Pattern

односно користи техники како PowerShell execution и DLL injection.
Campaign SDO
Campaign објектот ја претставува конкретната операција:
LockBit 4.0 Albanian Infrastructure Campaign
Во моделот постојат овие релации:
Campaign → attributed-to → Threat Actor
Campaign → targets → Identity

што значи дека кампањата е поврзана со LockBit operators и е насочена кон критична инфраструктура.
Attack Patterns
Attack Pattern објектите ги претставуваат техниките на напад, мапирани со MITRE ATT&CK.
Во моделот се вклучени:
    1. PowerShell Execution
MITRE ID: T1059.001
    2. DLL Injection
MITRE ID: T1055.001
Овие техники се користат од LockBit malware за:
    • извршување на злонамерен код
    • bypass на безбедносни механизми
    • инјектирање код во легитимни процеси.
Indicators
Indicator објектите претставуваат Indicators of Compromise (IOC).
Во моделот се користат SHA-256 hash вредности за:
    • PowerShell скрипти
    • extracted malware фајлови
    • DLL компоненти
Во моделот постојат овие релации:
Indicator → indicates → Malware

што значи дека тие можат да се користат за детекција на LockBit malware во системите.

Со STIX Relationship Objects (SRO) се прикажани логичките врски помеѓу главните објекти на нападот. Релациите uses, targets, attributed-to и indicates овозможуваат структурирано претставување на односите помеѓу: Identity, threat-actor, campaign,  malware, attack-pattern 
Релации:
uses, targets, attributed-to и indicates 

