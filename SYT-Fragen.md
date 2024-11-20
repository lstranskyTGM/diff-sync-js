# Fragen

**Autoren:** Kacper Boahczyk, Leo Stransky  
**Version:** 20. November 2024

---

## Allgemeine Fragen

1. **Welche Implementierung des Diff-Patch-Algorithmus wird verwendet?**

2. **Wo werden die Dokumente und ihre Schattenkopien gespeichert?**

3. **Wie und warum kann der Synchronisierungszyklus angepasst werden?**
    - **Vorteile:**
    - **Nachteile:**

4. **Wo und wie ist der Edit-Stack implementiert?**
    - **Client-Seite:** Im `diffSync.onSend({...}`
    - **Server-Seite:** Im `diffSync.onReceive({...}`

5. **Ist es möglich, eine Peer-to-Peer-Version von Herrn Wei's Implementierung bereitzustellen?**

6. **Kann die API in anderen JavaScript-Projekten verwendet werden?**
    - Falls ja, wie?

7. **Sind die JSON-Dokumente mit anderen Dokumenttypen austauschbar?**

8. **Wie behandelt Herr Wei Konfliktlösungen?**

9. **Welche potenziellen Verbesserungen könnten an Herrn Wei's Code vorgenommen werden?**

10. **Ist es möglich, diff-sync.js mit einer dokumentorientierten NoSQL-Datenbank zu kombinieren?**
