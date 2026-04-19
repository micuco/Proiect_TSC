# Proiect_TSC
InkTime este un smartwatch low-cost, open-source, bazat pe microcontroller-ul nRF52840. Proiectul acopera intreg procesul de dezvoltare hardware, de la schema electrica pana la integrarea mecanica intr-o carcasa.

Sistemul este compus din urmatoarele blocuri principale: MCU nRF52840, Power Management (LiPo Charger + DC/DC), IMU, E-paper Display + Driver, Fuel Gauge, USB-C + ESD Protection, Haptic Driver, Butoane, Interfata SWD.

Microcontroller-ul principal gestioneaza: comunicatia BLE, interfata SPI pentru display, I2C pentru senzori (IMU, fuel gauge),USB pentru alimentare si debug.

Sistemul de alimentare include: BQ25180 pentru incarcarea bateriei LiPo, RT6160 pentru conversie DC/DC, multiple condensatoare de decuplare (100nF, 1uF, 4.7uF). Traseele de alimentare sunt dimensionate conform cerintelor (min 0.3mm).

IMU (BMA421): conectat pe I2C (SDA, SCL), semnale de intrerupere: INT1, INT2, utilizat pentru detectarea miscarii si gesturilor.

E-Paper Display: conectare prin SPI (MOSI, SCK, CS, DC, RST), driver dedicat pentru generarea tensiunilor necesare (boost circuit).

Fuel Gauge: monitorizeaza nivelul bateriei, conectat pe I2C, pin ALERT pentru notificari.

Haptic Driver: DRV2605 pentru control vibratii, control prin I2C, semnal enable din MCU.

USB-C: folosit pentru alimentare si comunicatie, protejat cu circuit ESD dedicat.

Butoane: 3 butoane, conectate la GPIO cu rezistente pull-up/pull-down.

Pin Mapping (nRF52840):

| Functie       | Pin     |
| ------------- | ------- |
| I2C SDA       | P0.xx   |
| I2C SCL       | P0.xx   |
| SPI MOSI      | P0.xx   |
| SPI SCK       | P0.xx   |
| EPD CS/DC/RST | GPIO    |
| IMU INT       | GPIO    |
| SWDIO         | dedicat |
| SWDCLK        | dedicat |

Design Decisions: folosirea e-paper pentru consum redus, integrarea fuel gauge pentru autonomie, antena externa pozitionata la marginea PCB-ului, separarea clara a planurilor de masa.

DRC & ERC: verificari efectuate, respectate regulile de routare, fara unghiuri de 90, condensatoare de decuplare aproape de IC-uri.

PCB Design: PCB 2 layer (TOP + BOTTOM), plan de masa pe ambele layere, via stitching pentru GND, componente plasate pe TOP, trasee: power: ≥ 0.3mm, semnal: ≥ 0.15mm, antena: plasata la marginea PCB, fara plan de masa sub ea.

Modelul 3D include: PCB complet cu componente, baterie LiPo (modelata conform datasheet), display e-paper, carcasa smartwatch.

Integrarea presupune: alinierea butoanelor cu carcasa, pozitionarea corecta a USB-C, fixarea bateriei pe test pads, verificarea spatiului intern si a interferentelor..

