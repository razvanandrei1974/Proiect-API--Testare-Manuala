# API-Testing - Oblio Software 
![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/dafe1edf-cbad-4580-98fc-2282a6725875)


## 🎌 Autorization Token
![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/30156934-3084-450d-b339-83878c88b52a)
![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/c6b43356-d73d-4d87-b8c9-a97bfd4c68dd)



# ▶️ Results 

![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/a748736f-e216-449b-a86b-2e2b4ba3368f)


## ▶️ Detailed tests

![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/41bc976a-5bbe-480a-a2a5-ea11769136d1)
![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/cec643cd-36d6-457a-9fee-e620f72f86aa)
![image](https://github.com/razvanandrei1974/Proiect-API--Testare-Manuala/assets/144438182/e04deb63-b125-49a4-a723-3ac85bbd2337)





# ‼️ Test Plan 

# API Documnentation - Oblio Software

# :pushpin: Prezentare generala

Scopul API
Oblio pune la dispozitie pentru dezvoltatori un API cu ajutorul caruia puteti avea acces la diferite facilitati cum ar fi:
•	Vizualizare nomenclatoare;
•	Emitere proforme, avize, facturi, facturi pe baza de proforma sau aviz;
•	Vizualizare factura, proforma sau aviz;
•	Anulare factura, proforma sau aviz;
•	Restaurare factura, proforma sau aviz;
•	Stergere factura, proforma sau aviz;
Raspunsurile vin in format JSON, daca cererea a fost facuta cu succes se va trimite de catre server un cod de status 200, daca cererea nu este facuta cu succes se va trimite un cod de status 400 sau 401 cu un mesaj de eroare.
Pe pagina noastra de GitHub https://github.com/OblioSoftware veti gasi exemple de implementare ale API-ului.
Autorizare

## 📌 Generare token de acces
### _https://www.oblio.eu/api/authorize/token - POST_
Oblio REST API foloseste modulul OAuth 2.0 pentru autorizare. Acesta are nevoie de parametrul "client_id" care reprezinta email-ul cu care va autentificati in Oblio si "client_secret" care este un token pe care il gasiti in cont in sectiunea "Setari" > "Date Cont". Pentru securitate, token-ul "client_secret" se regenereaza de fiecare data cand se reseteaza parola. Pentru obtinerea token-ului de acces se trimite o cerere prin metoda "POST" impreuna cu parametrii "client_id" si "client_secret" catre adresa https://www.oblio.eu/api/authorize/token
Toate celelalte cereri catre Oblio REST API se fac folosind header-ul "Authorization" cu valoarea "Bearer {access_token}" unde {access_token} se obtine din cererea de mai sus.

## Nomenclatoare

## Nomenclator companii
### _https://www.oblio.eu/api/nomenclature/companies - GET_
Returneaza lista de companii asociate cu contul Oblio

## Nomenclator cote TVA
### _https://www.oblio.eu/api/nomenclature/vat_rates - GET_
Returneaza lista de cote TVA pentru o anumita firma
PARAMETRU	EXPLICATIE
cif *	CIF-ul firmei

## Nomenclator clienti
### _https://www.oblio.eu/api/nomenclature/clients - GET_
Returneaza lista de clienti pentru o anumita firma
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* name	Numele clientului cautat
+ clientCif	Ciful clientului cautat
- offset	Vor aparea initial maxim 250 de rezultate, este de preferat sa fie multiplu de 250 (0, 250, 500 etc.), valoarea implicita este 0

## Nomenclator produse
### _https://www.oblio.eu/api/nomenclature/products - GET_
Returneaza lista de produse pentru o anumita firma. Pentru servicii nu se tine cont de gestiunea unde se afla si deci nu apare rubrica "stock".
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* name	Numele produsului cautat
+ code	Codul produsului cautat
- management	Gestiunea in care se face cautarea (La folosirea acestui parametru produsele vor aparea listate ca serviciile)
  workStation	Punctul de lucru al gestiunii in care se face cautarea

## Nomenclator serii documente
### _https://www.oblio.eu/api/nomenclature/series - GET_
Returneaza lista de serii documente pentru o anumita firma
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei

## Nomenclator limbi
### _https://www.oblio.eu/api/nomenclature/languages - GET_
Returneaza lista de limbi straine pentru o anumita firmaPARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei

## Nomenclator gestiuni
### _https://www.oblio.eu/api/nomenclature/management - GET_
Returneaza lista de gestiuni pentru o anumita firma, functioneaza doar daca sunt activate stocurile
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei

## 📌 Emitere documente

## Emitere proforma
Emiterea de documente folosind Oblio REST API se face prin metoda POST trimitand datele in forma RAW in format JSON.

### _https://www.oblio.eu/api/docs/proforma - POST_
Emiterea proformelor se face cu urmatorii parametrii:
Parametri document
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei de unde se emit facturi. Il gasiti la Oblio.eu > Setari > Date firma
* client *	Necesita anumiti parametri. Acestia se gasesc in zona "Parametri client"
+ issueDate	Data emiterii in format AAAA-LL-ZZ, valoare implicita este ziua curenta
- dueDate	Data scadentei in format AAAA-LL-ZZ
* seriesName *	Nume serie document (se gaseste in nomenclator serii documente)
+ language	Codul de limba in care se emite factura (se gasesc limbile disponibile in nomenclator), valoarea implicita este "RO"
- precision	Precizia documentului. Trebuie sa fie un numar intreg cu valoarea intre 2 si 4, valoarea implicita este 2
* currency	Moneda documentului, valoarea implicita este "RON"
+ exchangeRate	Rata de schimb in cazul documentelor in valuta, valoare implicita este cursul setat in setarile companiei
- products	Este un tablou cu produse. Parametrii pentru produse se gasesc in zona "Parametri produs"
* issuerName	Intocmit de
+ issuerId	CNP-ul celui care a intocmit documentul
- noticeNumber	Nr. aviz insotire
* internalNote	Nota interna (nu va fi vizibila pentru client)
+ deputyName	Delegat
- deputyIdentityCard	Carte Identitate delegat
* deputyAuto	Auto delegat
+ selesAgent	Agent vanzari
- mentions	Mentiuni
* workStation	Punct de lucru. Este valabil doar dupa activarea stocurilor, valoarea implicita este "Sediu"
+ sendEmail	Daca are valoarea 1 se va trimite email-ul de la Setari > E-mail-uri alarma > Document prin email
Parametri client
PARAMETRU	EXPLICATIE
- cif	CIF-ul firmei sau CNP-ul clientului
* name *	Numele (pentru persoanelor fizice) sau a numele firmei (pentru persoane juridice)
+ rc	Numar Registru Comert
- code	Cod client
* address	Adresa
+ state	Judet
- city	Oras
* country	Tara
+ iban	IBAN
- bank	Banca
* email	Email
+ phone	Numar de telefon
- contact	Persoana de contact
* vatPayer	Platitor de TVA, ia valorile 0 sau 1
save	Sa schimbe sau nu datele clientului, ia valorile 0 sau 1. Valoarea implicita este 0
autocomplete	Daca este completat parametrul "cif" cu o firma din Romania, datele se preiau automat, ia valorile 0 sau 1. Valoarea implicita este 0
Parametri produs
PARAMETRU	EXPLICATIE
- name *	Numele produsului
* code	Codul produsului
+ description	Descrierea
- price *	Pretul
* measuringUnit	Unitatea de masura a produsului, valoarea implicita este "buc"
+ currency	Moneda
exchangeRate	Rata de schimb a monezii in cazul in care aceasta este diferita de moneda documentului
- vatName	Numele cotei de TVA (se gaseste in nomenclator cote TVA)
* vatPercentage	Procentul cotei de TVA (se gaseste in nomenclator cote TVA)
+ vatIncluded	TVA-ul este inclus in pretul produsului, ia valorile 0 sau 1, valoarea implicita este 1
- quantity	Cantitatea, valoare implicita este 1
* management	Numele gestiunii din care face parte produsul. Este valabil doar dupa activarea stocurilor pentru produse stocabile (nu este valabil pentru servicii)
+ productType	Tip produs. Trebuie sa fie unul din "Marfa", "Materii prime", "Materiale consumabile", "Semifabricate", "Produs finit", "Produs rezidual", "Produse agricole", "Animale si pasari", "Ambalaje", "Obiecte de inventar", "Serviciu". Este valabil doar dupa activarea stocurilor
- nameTranslation	Numele produsului tradus (daca este cazul pentru facturile in alte limbi decat romana)
* measuringUnitTranslation	Unitatea de masura tradusa (daca este cazul pentru facturile in alte limbi decat romana)
+ save	Salveaza pretul de lista. Poate sa fie 0 sau 1. Valoarea implicita este 1

## 📌 Discounturi

Sunt elemente in lista de produse si au urmatorii parametrii:
PARAMETRU	EXPLICATIE
- name *	Numele care apare in dreptul discountului
* discountType	Discount procentual sau valoric, ia valorile "procentual" sau "valoric", valoarea implicita este "valoric"
+ discount *	Valoare discount
- discountAllAbove	Ia valoarea 1 daca este valabil pentru toate produsele fara discount dinaintea sa sau 0 doar pentru primul produs de deasupra sa, valoarea implicita este 0

## Emitere avize
### _https://www.oblio.eu/api/docs/notice - POST_
Emiterea avizelor se face identic cu emiterea proformelor cu diferenta ca avizele nu au parametrul "noticeNumber" si au optiunea (in cazul in care este activat stocul) de a folosi parametrul "useStock" care are valoarea implicita 1

## Emitere facturi
### _https://www.oblio.eu/api/docs/invoice - POST_
Emiterea facturilor se face identic cu emiterea proformelor cu diferenta ca facturile mai au si urmatorii parametrii:
Parametri document
PARAMETRU	EXPLICATIE
- deliveryDate	Data livrarii in format AAAA-LL-ZZ
* collectDate	Data incasarii in format AAAA-LL-ZZ
+ referenceDocument	Document de referinta in cazul generarii de facturi pe baza de proforma sau de aviz. Vezi "Parametri document de referinta"
- collect	Incasare document. Vezi "Parametri incasare document"
* useStock	Descarcare pe gestiune (in cazul in care este activat stocul). Poate fi 0 sau 1
Parametri document de referinta
PARAMETRU	EXPLICATIE
- type *	Tipul documentului de referinta (Factura, Proforma sau Aviz)
* seriesName *	Numele seriei documentului de referinta
+ number *	Numarul seriei documentului de referinta
- refund	Sterge incasarea asociata cu factura stornata pentru "type" = "Factura". Poate fi 0 sau 1
Parametri incasare document
PARAMETRU	EXPLICATIE
- type *	Tipul de document cu care se face incasarea. Poate fi "Chitanta", "Bon fiscal", "Alta incasare numerar", "Ordin de plata", "Mandat postal", "Card", "CEC", "Bilet ordin", "Alta incasare banca"
* seriesName	Numele seriei chitantei. Trebuie definita in cazul in care incasarea se face prin chitanta
+ documentNumber	Numarul documentului de incasare. Trebuie definit in cazul in care incasarea nu se face prin chitanta
- value	Valoarea incasata, valoarea implicita este totalul facturii care urmeaza sa fie incasata
* issueDate	Data emiterii in format AAAA-LL-ZZ, valoare implicita este ziua curenta (valabil pentru incasare factura)

## 📌Mentiuni
## Incasare factura
Incasare factura

### _https://www.oblio.eu/api/docs/invoice/collect - PUT_
Incasare facturilor se face cu urmatorii parametrii:
Parametri incasare factura
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Numele seriei documentului
+ number *	Numarul seriei documentului
- collect *	Incasare document. Vezi "Parametri incasare document"

## 📌 Vizualizare documente

## Vizualizare factura
### _https://www.oblio.eu/api/docs/invoice?cif={cif}&seriesName={seriesName}&number={number} - GET_
Parametri vizualizare document
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Numele seriei documentului
+ number *	Numarul seriei documentului
Vizualizare proforma
https://www.oblio.eu/api/docs/proforma?cif={cif}&seriesName={seriesName}&number={number} - GET
Parametrii sunt aceiasi ca la vizualizare factura

## Vizualizare aviz
### _https://www.oblio.eu/api/docs/notice?cif={cif}&seriesName={seriesName}&number={number} - GET_
Parametrii sunt aceiasi ca la vizualizare factura


## 📌 Anulare documente

## Anulare factura
### _https://www.oblio.eu/api/docs/invoice/cancel - PUT_
Parametri anulare document
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Numele seriei documentului
+ number *	Numarul seriei documentului

## Anulare proforma
### _https://www.oblio.eu/api/docs/proforma/cancel - PUT_
Parametrii sunt aceiasi ca la anulare factura

## Anulare aviz
### _https://www.oblio.eu/api/docs/notice/cancel - PUT_
Parametrii sunt aceiasi ca la anulare factura
Restaurare documente
Restaurare factura
https://www.oblio.eu/api/docs/invoice/restore - PUT
Parametri restaurare document
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Numele seriei documentului
+ number *	Numarul seriei documentului
Restaurare proforma
https://www.oblio.eu/api/docs/proforma/restore - PUT
Parametrii sunt aceiasi ca la restaurare factura

## Restaurare aviz
### _https://www.oblio.eu/api/docs/notice/restore - PUT_
Parametrii sunt aceiasi ca la restaurare factura


## 📌 Stergere documente

## Stergere factura
### _https://www.oblio.eu/api/docs/invoice - DELETE_
Functia de stergere se poate folosi doar pentru ultimul document din serie.
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Numele seriei documentului
+ number *	Numarul seriei documentului

## Stergere proforma
### _https://www.oblio.eu/api/docs/proforma - DELETE_
Parametrii sunt aceiasi ca la stergere factura
## Stergere aviz
### _https://www.oblio.eu/api/docs/notice - DELETE_
Parametrii sunt aceiasi ca la stergere factura

## 📌 Raport documente

## Listare facturi
### _https://www.oblio.eu/api/docs/invoice/list - GET_
Functia de listare a facturilor emise in Oblio.
Parametri listare documente
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName	Filtru dupa Numele seriei
+ number	Filtru dupa Numarul documentului
- id	Filtru dupa id
* draft	Filtru dupa Document draft. Poate lua valorile -1 - este ignorat, 0 - nu sunt draft, 1 - sunt draft
+ client	Filtru dupa Client. Contine un array/map cu "cif", "email", "phone" sau "code"
- canceled	Filtru dupa Document anulat. Poate lua valorile -1 - este ignorat, 0 - nu sunt anulate, 1 - sunt anulate
* issuedAfter	Filtru dupa Data de inceput in format AAAA-LL-ZZ
+ issuedBefore	Filtru dupa Data de sfarsit in format AAAA-LL-ZZ
- withProducts	Include si produsele din factura in rezultat
* withEinvoiceStatus	Include status-ul facturilor din SPV
+ orderBy	Ordonare dupa: id, issueDate, number
- orderDir	Ordonare ASC/DESC
* limitPerPage	Rezultate pe pagina. Maxim 100
+ offset	Vor aparea initial maxim 100 de rezultate, este de preferat sa fie multiplu de 100 (0, 100, 100 etc.), valoarea implicita este 0

## 📌 SPV

## Trimite factura in SPV
### _https://www.oblio.eu/api/docs/einvoice - POST_
Functia de Trimite factura in SPV pentru facturile emise in Oblio.
Parametri pentru Trimite factura in SPV
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Filtru dupa Numele seriei
+ number *	Filtru dupa Numarul documentului

## Descarca arhiva SPV
### _https://www.oblio.eu/api/docs/einvoice - GET_
Functia de descarcare arhiva SPV pentru facturile emise in Oblio.
Parametri descarcare arhiva SPV
PARAMETRU	EXPLICATIE
- cif *	CIF-ul firmei
* seriesName *	Filtru dupa Numele seriei
+ number *	Filtru dupa Numarul documentului


