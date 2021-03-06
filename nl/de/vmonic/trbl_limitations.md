---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Zusätzliche Einschränkungen und Hinweise

Prüfen Sie die folgenden Hinweise und Einschränkungen, wenn Sie mit {{site.data.keyword.vmwaresolutions_full}} arbeiten.

## Automatische Installation von Windows-Updates

Microsoft Active Directory (AD) bzw. der Domänennamensserver (DNS) wird automatisch für das Herunterladen von Updates konfiguriert. Weder die Installation dieser Updates noch der Warmstart wird automatisch durchgeführt. Sie müssen die Updates manuell installieren und den Warmstart zu einem geplanten Zeitpunkt ausführen, zu dem Unterbrechungen der laufenden AD-Serverkonfiguration und anderen Sicherungsjobs vermieden werden. Um Windows-Updates anzuwenden, installieren Sie die Updates manuell.

## Hinweise zur Auswahl eines Rootdomänennamens für Cloud Foundation-Instanzen

Wenn Sie während der Bereitstellung einer primären oder sekundären Cloud Foundation-Instanz einen Domänennamen auswählen, müssen Sie sicherstellen, dass der Hostname `sddcmanager.<subdomain>` bei Verwendung der Befehle `ping` oder `nslookup` nicht in eine externe Domäne aufgelöst wird.

Die Struktur der Unterdomäne für die Cloud Foundation-Instanz lautet `<VCF instance name>.<domain name>`. Falls beispielsweise für `<domain name>` der Wert `test.local` angegeben wird und Ihre Cloud Foundation-Instanz `mytest` heißt, darf der Hostname `sddcmanager.mytest.test.local` nicht in eine IP-Adresse aufgelöst werden, bevor die Cloud Foundation-Instanz bereitgestellt wird. Andernfalls kann die Bereitstellung der Instanz fehlschlagen.
