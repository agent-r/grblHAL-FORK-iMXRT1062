## INSTALL:

1) Ordner erstellen
2) Ordner in VsCode öffnen
3) Terminalfenster öffnen
3) git clone --recurse-submodules https://github.com/agent-r/grblHAL-FORK-iMXRT1062.git

## Änderungen im Code:

1) my_machine.h > change/uncomment:

```
#define BOARD_T41U5XBB

#define Y_GANGED             1
#define Y_AUTO_SQUARE        1

```

2) my_machine.h > insert at the end of file:

```
////////////////////////////////
//       OWN DEFINITONS       //
////////////////////////////////

#define N_AXIS 4                      //  grbl/config.h
#define OVERRIDE_BUFSIZE 128          //  grbl.hal/override.h

#define PENDANT_ENABLE      1         //  grbl/plugins_init.h

#define SERIAL_PORT	6    // PORT 6 routes to PIN 0 and 1
// #define UART1_RX    	(0u) // not used, info only. for BLE-ESP32
// #define UART1_TX    	(1u) // not used, info only. for BLE-ESP32
```

3)  grbl/plugins_init.h > insert at the beginnig of file:

```
    #if PENDANT_ENABLE
       extern void pendant_init (void);
       pendant_init();
    #endif
```
  

## Weiteres Vorgehen:

1) compilieren und hochladen
2) Connect via Serial (115200)
3)  Einstellungen in GRBL ändern?

    - $6=1 (invert Probe Pin)
    - $5=7 (invert XYZ-Endstop)
    - $14=70 (invert Hold, Spindle, E-Stop)



