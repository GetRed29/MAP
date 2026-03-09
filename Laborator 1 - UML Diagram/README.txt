Order Management System Modeling
Descriere generală

Acest proiect modelează un sistem de gestiune a comenzilor care, în forma inițială, prezintă mai multe probleme de design software, cum ar fi existența unei God Class (cuplare mare între componente și responsabilități amestecate în aceeași clasă). Scopul modelării a fost înțelegerea structurii actuale a sistemului și propunerea unei arhitecturi îmbunătățite prin refactorizare.

Diagramele realizate ilustrează atât funcționalitățile sistemului, cât și structura internă a acestuia înainte și după refactorizare, precum și fluxurile principale de execuție.



Decizii de modelare

1. Identificarea actorilor și a cazurilor de utilizare

În diagrama de cazuri de utilizare au fost identificați trei actori principali:

Client – utilizatorul care interacționează cu sistemul pentru a vizualiza produse, a adăuga produse în coș și a plasa sau anula comenzi.

Admin – responsabil pentru administrarea produselor și vizualizarea comenzilor din sistem.

Sistem de plată – sistem extern utilizat pentru procesarea plăților.


Au fost definite mai multe cazuri de utilizare relevante pentru funcționarea sistemului, precum:

vizualizarea produselor;

adăugarea produselor în coș;

plasarea unei comenzi;

procesarea plății;

anularea unei comenzi;

administrarea produselor.

Relațiile «include» au fost folosite pentru funcționalități obligatorii ale unui caz de utilizare (de exemplu procesarea plății în timpul plasării unei comenzi), iar relațiile «extend» pentru comportamente opționale sau condiționale (de exemplu trimiterea emailului de confirmare).



2. Modelarea structurii inițiale a sistemului

În diagrama de clasă „before refactoring” a fost reprezentată structura existentă a sistemului. În această variantă apare o clasă centrală, OrderManager, care gestionează multiple responsabilități:

logica de business pentru comenzi;

procesarea plăților;

trimiterea emailurilor;

accesul la baza de date.



Această structură conduce la mai multe probleme de design:

existența unei God Class;

cuplare puternică între componente;

responsabilități multiple într-o singură clasă;

dificultate în testare și mentenanță.




3. Refactorizarea arhitecturii

Pentru a îmbunătăți designul sistemului, responsabilitățile au fost separate în mai multe componente specializate.

Principalele decizii au fost:

introducerea unui OrderController pentru gestionarea cererilor venite din partea clientului;

mutarea logicii de business în OrderService;

separarea procesării plăților într-un PaymentService;

utilizarea unui EmailService pentru trimiterea notificărilor;

izolarea accesului la baza de date într-un OrderRepository.



Această structură reduce cuplarea dintre componente și face sistemul mai ușor de extins și testat.




4. Modelarea fluxurilor principale

Au fost create două diagrame de secvență pentru a descrie comportamentul sistemului în scenarii importante:

Plasarea unei comenzi

clientul trimite o cerere de plasare a comenzii;

sistemul procesează plata;

comanda este salvată în baza de date;

opțional este trimis un email de confirmare.



Anularea unei comenzi

sistemul verifică starea comenzii

dacă comanda a fost deja expediată, anularea nu este permisă

dacă anularea este permisă, comanda este anulată și se inițiază rambursarea plății



În diagrame au fost utilizate blocurile alt pentru fluxuri alternative și opt pentru comportamente opționale.




Concluzie

Prin realizarea acestor diagrame a fost posibilă evidențierea problemelor de design ale sistemului inițial și propunerea unei structuri mai clare și mai modulare. Separarea responsabilităților și reducerea dependențelor directe dintre componente contribuie la un sistem mai ușor de întreținut, testat și extins în viitor.