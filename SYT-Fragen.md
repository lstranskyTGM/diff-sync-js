# Fragen

**Autoren:** Kacper Boahczyk, Leo Stransky  
**Version:** 20. November 2024

---

## Allgemeine Fragen

1. **Welche Implementierung des Diff-Patch-Algorithmus wird verwendet?**

2. **Wo werden die Dokumente und ihre Schattenkopien gespeichert?**

Die Dokumente werden im mainText gespeichert, wobei die Schattenkopien in den Container-Objekten gespeichert werden.

3. **Wie und warum kann der Synchronisierungszyklus angepasst werden?**

Er befindet sich unter dem Client in index.html → Zeile 40.    Es ist in unter dem Client bei index.html --> line 40 -- Stanartwert ist 250

   Bei änderungen vergrößert oder verkleinert sich die Delay bei synchroniezieren der Patchs.

   Der  Standardwert hierbei  ist 250.

Bei Änderungen vergrößert oder verkleinert sich die Verzögerung beim Synchronisieren der Patches.
4. **Wo und wie ist der Edit-Stack implementiert?**
    - **Client-Seite:** Im `diffSync.onSend({...}`
      - Edits are prepared and sent to the server.
     - **Server-Seite:** Im `diffSync.onReceive({...}`
       - Patches are applied to the shadow and main copies, and new edits are sent back to clients.


5. **Ist es möglich, eine Peer-to-Peer-Version von Herrn Wei's Implementierung bereitzustellen?**

Ja, wenn man auf ein verteiltes Shadow-Management umsteigt.

6. **Kann die API in anderen JavaScript-Projekten verwendet werden?**
    - Falls ja, wie?

7. **Sind die JSON-Dokumente mit anderen Dokumenttypen austauschbar?**

Nein, man müsste eine andere Patch-Logik implementieren, da unter dem Server die "fast-json-patch"-Logik verwendet wird.


8. **Wie behandelt Herr Wei Konfliktlösungen?**

Bei Konflikten kehrt Wei zur ursprünglichen Version zurück. 
Dies erfolgt durch ein Backup in diffSync.js in den Zeilen 124 bis 141, oder er verwirft die Änderungen komplett.

9. **Welche potenziellen Verbesserungen könnten an Herrn Wei's Code vorgenommen werden?**

Es kann das Problem mit verlorenen Rückgabe-Paketen auftreten.

10. **Ist es möglich, diff-sync.js mit einer dokumentorientierten NoSQL-Datenbank zu kombinieren?**
