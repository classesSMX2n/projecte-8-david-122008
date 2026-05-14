# Pla de Transformació Digital

## 1. Mapa de Processos

Hem optat per un model híbrid de mobilitat, prioritzant la rapidesa i l'eliminació d'errors humans.

**Pas 1:**  
El cambrer utilitza una tablet/smartphone a peu de taula. La comanda es sincronitza instantàniament via Wi-Fi amb el TPV central.

**Pas 2:**  
La comanda es divideix automàticament. Les begudes s'imprimeixen (o apareixen en pantalla) a la barra i el menjar a la cuina.

**Pas 3:**  
Quan tot sigui llest, el sistema notifica al cambrer. Finalment es lliura el producte.

**Pas 4:**  
Quan el client demana el compte, es genera el tiquet des del TPV o impressora de cinturó i es processa el pagament.

---

## 2. Disseny de la Xarxa

Per garantir la seguretat de les dades bancàries i oferir un servei d'alta qualitat per a teletreballadors, implementarem una segmentació mitjançant VLANs.

### Arquitectura de xarxa

**VLAN 10 (Staff/Admin):**  
  Xarxa oculta i xifrada per a TPVs, datàfons i impressores. Prioritat de trànsit alta (QoS).

**VLAN 20 (Wifi clients):**  
  Xarxa oberta amb portal captiu.

**Portal Captiu:**  
  Abans de navegar, el client veu una pantalla de benvinguda amb el logo de la cafeteria i una promoció actual. Cal acceptar els termes d'ús.

**Aïllament (Client Isolation):**  
  Els clients no poden veure's entre ells ni accedir als equips de l'empresa, ja que estan en una xarxa diferent.

---

## 3. Pressupost de Hardware

| Element                         | Descripció                                      | Unitats | Preu Unitari | Total |
|--------------------------------|--------------------------------------------------|--------|--------------|-------|
| TPV Central + calaix efectiu   | Pantalla tàctil 15" IP65 (resistent a líquids)  | 1      | 650€         | 650€  |
| Tablets                        | Dispositius mòbils Android “Motorola moto-g86 5G” | 2      | 199€         | 398€  |
| Router                         | Ubiquiti UniFi Dream Machine                    | 1      | 350€         | 350€  |
| Punt d'Accés                   | UniFi WiFi 6 Pro (suporta +300 usuaris)         | 1      | 180€         | 180€  |
| **Total Hardware**             |                                                  |        |              | **1.578€** |

---

## 4. Informe de Software

### Opcions analitzades

**Software Lliure (Odoo Community / Floreant POS):**  
  Sense llicència mensual, però requereix un servidor local i manteniment tècnic propi.

**Software Comercial (Revo / Square):**  
  Pagament per subscripció (SaaS), suport 24/7 i actualitzacions al núvol incloses.

### Comparativa de Costos (S’acumulen amb els anys)

| Període | Software Lliure (Instal·lació + Manteniment) | Software Comercial Revo (~79€/mes) |
|--------|----------------------------------------------|-----------------------------------|
| Any 1  | 1.200€ (setup inicial del servidor)           | 948€                              |
| Any 3  | 2.400€ (any 1 + manteniment)                 | 2.844€                            |

### Conclusió

El software lliure és més rendible a partir del segon any, però el software comercial (com Revo) ofereix més estabilitat i suport del desenvolupador, reduint el risc de fallades.

---

## 5. Pla de Contingència

### Caiguda d'Internet

El sistema TPV i les impressores funcionen per xarxa cablejada, així la comunicació entre taula i cuina no s'atura.
Els datàfons moderns tenen SIM 4G/5G pròpia, per tant no necessiten Wi-Fi.
En cas extrem, es pot utilitzar temporalment llibreta i bolígraf.

### Fallada Elèctrica

Instal·lació d'un SAI per a l'ordinador de la caixa central i el router.
Permet tancar comptes oberts i continuar operant durant **30-60 minuts**.
