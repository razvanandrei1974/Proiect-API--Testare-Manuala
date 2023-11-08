# API-Testing

# Test Plan 

### INTRODUCERE
Pentru utilizarea API-ului de integrare selfAWB este necesar sa aveti incheiat un contract cu FAN Courier.
In cazul in care aveti un contract incheiat, insa nu ati primit datele de logare in aplicatia selfAWB, puteti contacta colegii de la Departamentul selfAWB la adresa selfawb@fancourier.ro.
In cazul in care nu aveti un contract incheiat cu FAN Courier si doriti acest lucru, puteti contacta colegii de la Departamentul Sales la adresa sales.bucuresti@fancourier.ro.
Pentru suport privind aceastra integrare puteti contacta colegii de la Departamentul Presales la adresa presales@fancourier.ro.
Pentru Autentificare se foloseste endpoint-ul Base Auth.

Pentru Generarea AWB-ului se folosesc endpoint-urile:
### 1. Tipuri Servicii
▪ se foloseste pentru a returna o lista cu tipurile de servicii
### 2. Optiuni Servicii
▪ se foloseste pentru a returna o lista cu optiunile ce pot fi utilizate pe un AWB, in functie de tipul de serviciu
### 3. Judete
▪ se foloseste pentru a returna o lista cu judetele din nomenclatorul FAN Courier
### 4. Localitati
▪ se foloseste pentru a returna o lista cu localitatile din nomenclatorul FAN Courier
### 5. Strazi
▪ se foloseste pentru a returna o lista cu strazile din nomenclatorul FAN Courier
### 6. AWB Intern
▪ se foloseste pentru a genera AWB-uri Interne
### 7. Puncte PUDO
▪ se foloseste pentru a obtine o lista cu punctele fixe FANbox/PayPoint
### 8. AWB Extern
▪ se foloseste pentru a genera AWB-uri de Export
### 9. Printare AWB
▪ se foloseste pentru a printa AWB-urile
### 10. Stergere AWB
▪ poate fi utilizat pentru a sterge un AWB din borderou
### Pentru plasarea sau anularea unei Comenzi de Curier se folosesc endpoint-urile:
▪ Plasare Comanda Curier
▪ Stergere Comanda Curier
### Pentru Raportare - Expeditii se folosesc endpoint-urile:
▪ Borderou
▪ Event-uri AWB
▪ AWB Tracking
▪ Viramente bancare
### Pentru Raportare - Comenzi se folosesc endpoint-urile:
▪ Raport Comenzi
▪ Event-uri Comenzi Curier
▪ Tracking Comenzi Curier
### Pentru a genera comenzi de Retur se folosesc detaliile din sectiunea Expeditii de

## AUTENTIFICARE
Descriere : generare token; acesta are termen de valabilitate 24h si trebuie refacut dupa expirare
Metoda : HTTP POST
Response : JSON
Important : Se va folosi ca Bearer Token pentru autentificarea si autorizarea fiecarui endpoint
Params:
• username – numele de utilizator folosit la logarea in aplicatia selfAWB
• password – parola folosita la logarea in aplicatia selfAWB


[Test Plan Fun Courier](https://github.com/razvanandrei1974/API-Testing/blob/main/RO_FANCourier_API-2.0-100523.pdf)



![image](https://github.com/razvanandrei1974/API-Testing/assets/144438182/33b332a5-3d0c-4576-826d-4153ec21627c)

![image](https://github.com/razvanandrei1974/API-Testing/assets/144438182/5a552fd2-97db-4426-afaf-8c5f1a350813)

![image](https://github.com/razvanandrei1974/API-Testing/assets/144438182/0726e4eb-1b35-403d-8c5f-5a79bcd618e8)


