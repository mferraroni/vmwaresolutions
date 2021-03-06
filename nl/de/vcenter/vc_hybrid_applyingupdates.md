---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-05"

---

{:tip: .tip}

# Updates auf vCenter Server with Hybridity Bundle-Instanzen anwenden

Der Prozess zur Anwendung von Patches und Updates auf vCenter Server with Hybridity Bundle-Instanzen ist nur für die Managementkomponenten automatisiert. Die VMware-Updates müssen hingegen manuell angewendet werden.

## Vorbereitende Schritte

Bevor Sie versuchen, ein Update anzuwenden, erweitern Sie den Update-Eintrag, indem Sie auf den Abwärtspfeil klicken und die folgenden Informationen überprüfen:
* Überprüfen Sie die Version des Updates. Sie müssen die Updates in chronologischer Reihenfolge anwenden, also zuerst das älteste Update und zuletzt das neueste Update. Stellen Sie sicher, dass Sie alle vorherigen Updates angewendet haben, bevor Sie das aktuelle Update anwenden. Beispielsweise müssen Sie das Update für V2.3 anwenden, bevor Sie versuchen, das Update für V2.4 anzuwenden.
* Ermitteln Sie, ob eine Ausfallzeit erforderlich ist.
* Prüfen Sie die geschätzte Gesamtzeit für die Ausführung des Updates.
* Stellen Sie fest, wie sich das Update auf die virtuelle VMware-Umgebung auswirkt.
* Lesen Sie die Details über das Update.

Die folgende Tabelle zeigt, wie die verschiedenen Auswirkungsstufen das System beeinflussen.

Tabelle 1. Aktualisierungsstufen und Auswirkungen

| Aktualisierungsstufe  | Auswirkung        |  
|:------------- |:------------- |
| Niedrig    | Dieses Update hat keine Auswirkungen auf Systeme. Sie müssen es nicht während einer geplante Ausfallzeit anwenden. |  
| Mittel | Dieses Update kann sich auf einige Systeme auswirken. Es empfiehlt sich, es während einer geplanten Ausfallzeit anzuwenden. |  
| Bedeutend  | Dieses Update wirkt sich auf einige oder alle Systeme aus. Sie müssen es während einer geplanten Ausfallzeit anwenden. |  

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, die Sie aktualisieren wollen.
3. Überprüfen Sie auf der Seite **Zusammenfassung**, ob alle Instanzdetails korrekt angezeigt werden. Klicken Sie dann im linken Navigationsfenster auf **Infrastruktur**, um die Details auf der Seite **Infrastruktur** zu prüfen.
   Wenn die Details nicht angezeigt werden, kann dies auf ein Konnektivitätsproblem mit der virtuellen Maschine von IBM CloudDriver hinweisen, das aufgrund eines Problems mit einer Firewallregel oder aufgrund eines anderen Netzproblems aufgetreten ist. Lösen Sie das Problem, bevor Sie mit dem nächsten Schritt fortfahren, da das Update andernfalls fehlschlagen könnte.
4. Klicken Sie im linken Navigationsfenster auf **Update und Patch**.

   **Hinweis**: Die Seite **Update und Patch** enthält nur die Pakete für die Aktualisierung der IBM Managementkomponenten, nicht jedoch die VMware-Updates. {{site.data.keyword.vmwaresolutions_short}} wendet VMware-Updates für die folgenden Operationen an:
   * Wenn eine neue vCenter Server-Instanz bereitgestellt wird.
   * Wenn neue ESXi-Server hinzugefügt werden.
   * Wenn neue Cluster hinzugefügt werden.

5. Klicken Sie für Lizenzaktualisierungen auf **Aktualisierung der Lizenz**. Wählen Sie in der Liste die Edition aus, auf die das Upgrade durchgeführt werden soll, und klicken Sie dann auf **Upgrade**. Downgrades für Lizenzeditionen sind nicht verfügbar.

   **Hinweis:** Die Aktualisierung der Lizenz ersetzt alle vorhandenen NSX-Lizenzen in der Instanz. Zusätzliche Gebühren können bei einer Überschneidung von alten und neuen Lizenzen entstehen, wenn Sie ein Upgrade in der Mitte eines Abrechnungszyklus durchführen. Um zusätzliche Gebühren zu vermeiden, wird empfohlen, die Lizenz am Ende des Abrechnungszyklus zu aktualisieren.

6. Klicken Sie bei Software-Updates auf den Abwärtspfeil, um das Update zu erweitern, das Sie anwenden möchten, und führen Sie dann einen der folgenden Schritte aus:
   *  Um das Update sofort zu starten, klicken Sie auf das Überlaufmenüsymbol in der Spalte **Aktionen** des Update-Eintrags und anschließend auf **Update jetzt ausführen**.
   *  Um ein künftiges Update zu planen, klicken Sie auf das Überlaufmenüsymbol in der Spalte **Aktionen** des Update-Eintrags und anschließend auf **Update planen**. Wählen Sie das Datum, die Uhrzeit und die Zeitzone für den Start des Updates aus. Klicken Sie auf **OK**.
7. Wenn Sie Updates auf vCenter Server-Instanzen in Bereitstellungskonfigurationen mit mehreren Standorten anwenden, wird ein Abschnitt namens **Für Update erforderliche Schritte** angezeigt. In diesem Abschnitt werden die Updateoperationen aufgelistet, die für alle Instanzen in der Bereitstellung mit mehreren Standorten erforderlich sind. Sie müssen die Schritte nacheinander ausführen, indem Sie für jeden Schritt auf **Update anwenden** klicken. Vor dem Starten des nächsten Schritts müssen Sie warten, bis der vorherige Schritt abgeschlossen wurde.   

## Ergebnisse

1. Vor dem Start einer Updateoperation wird automatisch eine Sicherung der virtuellen Maschinen für das Management ausgeführt, falls für Ihre Instanz ein Sicherungsservice installiert ist. Nach Abschluss der Sicherung wird das Update angewendet.

2. Nachdem Sie ein Update angewendet haben, wird in der Statusliste der Software-Updates ein Eintrag angezeigt, der Aufschluss über den detaillierten Verarbeitungsfortschritt und den Status des Updates gibt. Sobald das Update erfolgreich abgeschlossen wurde, wird in der Liste der installierten Software-Updates ein Eintrag angezeigt.

  Um den aktuellen Status für einen Update-Job abzufragen, klicken Sie in der rechten oberen Ecke der Seite auf das Aktualisierungssymbol.
  {:tip}

3. Ausführliche Informationen zu den Statuswerten für Updates finden Sie in der folgenden Liste:
<dl class="dl">
<dt class="dt dlterm">Verfügbar</dt>
<dd class="dd">Das Update ist für eine Anwendung verfügbar. Sie können ein verfügbares Update erst dann auswählen, nachdem alle zugehörigen vorherigen Updates angewendet wurden.
</dd>
<dt class="dt dlterm">In Bearbeitung</dt>
<dd class="dd">Der Update-Job wurde initialisiert, ist aber noch nicht beendet. Sie können keine anderen Updates anwenden, bis der aktuelle Update-Job abgeschlossen ist.</dd>
<dt class="dt dlterm">Installiert</dt>
<dd class="dd">Der Update-Job ist abgeschlossen. Die entsprechende Komponente der VMware-Plattform wurde aktualisiert.</dd>
<dt class="dt dlterm">Fehlgeschlagen</dt>
<dd class="dd">Der Update-Job ist fehlschlagen. In der Konsole wird ein Fehler für das Fehlschlagen des Updates gemeldet. Überprüfen Sie den Fehler und lösen Sie das gemeldete Problem, bevor Sie das Update erneut anwenden.</dd>
<dt class="dt dlterm">Geplant</dt>
<dd class="dd">Der Update-Job ist für einen späteren Zeitpunkt geplant. Er wird am geplanten Zeitpunkt automatisch gestartet.</dd>
<dt class="dt dlterm">Unbekannt</dt>
<dd class="dd">Der Status des Update-Jobs kann nicht abgerufen werden. Bitten Sie den IBM Support um Unterstützung.</dd>
</dl>

4. Falls der Updateprozess bei einem bestimmten Schritt fehlschlägt, [wenden Sie sich an den IBM Support](../vmonic/trbl_support.html), um Unterstützung zu erhalten. Sie erhalten Hilfe bei der Lösung des Problems und Anweisungen, wie Sie das Upgrade ab dem fehlgeschlagenen Schritt erneut versuchen.

## Zugehörige Links

* [Überblick zu vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
