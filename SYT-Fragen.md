# Fragen

**Autoren:** Kacper Boahczyk, Leonhard Stransky  
**Version:** 20. November 2024

---

## Allgemeine Fragen

1. **Welche Implementierung des Diff-Patch-Algorithmus wird verwendet?**

Es wird die "Guaranteed Delivery Method" verwendet. 
Die Patches werden in einem Stack gespeichert, um sicherzustellen, dass keine Änderungen verloren gehen.

2. **Wo werden die Dokumente und ihre Schattenkopien gespeichert?**

**Dokumente:** werden im `mainText` gespeichert.

**Schattenkopien:** werden in den Container-Objekten gespeichert.

3. **Wie und warum kann der Synchronisierungszyklus angepasst werden?**

Der Synchronisierungszyklus befindet sich in der Datei `index.html` unter dem Client in der Zeile 40.

Der Standartwert liegt bei 250ms. Änderungen vergrößern oder verkleinern den Delay bei Patches.

- Ein kleinerer Wert führt zu einer schnelleren Synchronisierung und einer höheren Serverlast.
- Ein größerer Wert führt zu einer langsameren Synchronisierung und einer geringeren Serverlast.

4. **Wo und wie ist der Edit-Stack implementiert?**

- **Client-Seite:** Beim Senden von Patches in `diffSync.onSend({...})`
  - Die Edits werden vorbereitet und als Patches an den Server gesendet.
- **Server-Seite:** Beim Empfangen von Patches in `diffSync.onReceive({...})`
  - Die Patches werden auf die Schatten- und Hauptkopien angewendet.

5. **Ist es möglich, eine Peer-to-Peer-Version von Herrn Wei's Implementierung bereitzustellen?**

Ja, durch die Implementierung eines verteilten Shadow-Managements. 
Peer-Knoten könnten direkte Kommunikation verwenden, um Patches auszutauschen, ohne einen zentralen Server.

6. **Kann die API in anderen JavaScript-Projekten verwendet werden?**
    - Falls ja, wie?

Ja, durch Importieren des Moduls mit npm install diff-sync-js.

```javascript
import DiffSyncAlgorithm from 'diff-sync-js';
```

**Dokumentation:**
[README.md](https://github.com/wztech0192/diff-sync-js/blob/master/README.md)

7. **Sind die JSON-Dokumente mit anderen Dokumenttypen austauschbar?**

Ja, aber es erfordert Anpassungen der Patch-Logik. 
Derzeit wird json-fast-patch verwendet. 
Für andere Dokumenttypen (z. B. XML) müsste eine entsprechende Differenzierungs- und Patch-Strategie entwickelt werden.

8. **Wie behandelt Herr Wei Konfliktlösungen?**

Konflikte werden durch Wiederherstellung auf die vorherige Version gelöst.
Backups werden genutzt, um fehlerhafte Änderungen rückgängig zu machen (Zeilen 124–141 im Code).

9. **Welche potenziellen Verbesserungen könnten an Herrn Wei's Code vorgenommen werden?**

Es kann das Problem mit verlorenen Rückgabe-Paketen auftreten. Ein Protokoll zur Bestätigung von Patches könnte dieses Problem lösen.

Weiters könnten zusätzliche Dokumenttypen unterstützt werden, um die Flexibilität zu erhöhen.

10. **Ist es möglich, diff-sync.js mit einer dokumentorientierten NoSQL-Datenbank zu kombinieren?**

/
