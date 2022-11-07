# Timing-Pod_with_NTP_sync
Arduino RFID Timing POD with NTP sync via ESP8266

/**
 * Timing Pods record the Time to Racer Watches/cards upon scan of watch near RFID.
 * The Pods also display number of tags since switch on (useful for organisers and photographers etc)
 * as well as Temperature and battery voltage and battery status ('Good', 'OK' and 'Turn Off!')
 * The Status LED is solid when battery is good, flashing slowly when battery is OK and flashing fast when battery is about to die.
 * Upon a succesful scan POd will sound a Beep and corner LEDS will light up. No sound or LEDS= no Time written to watch!
 * 
 * This Program  has a 'Program mode' and a 'Timing mode'
 * DipSwitch Number 2 on the PCB toggles between the 2 modes.
 * Programming mode is used to sync the RTC time to the PC time using the 'Processing' program 'SyncArduinoClock'
 * Programming mode is also used to set the Stage ID (Stage 1 Start, Stage 2 Finish etc)by swiping a watch/tag during the count down
 * Timing Mode is used to write the RTC time to racer watch/card. Times are recorded to specific sectors on the watch according to the
 * Stage ID and latest scan will overwrite previous times!
 * 
 * Old way To Sync The RTC Time to PC Timevia processing program called SyncArduinoClock.pde:
 * 1)Put POD in programming mode (dipswitch 2)
 * 2) Open up 'Processing' program open file 'SyncArduinoClock'
 * 3)Plug FTDI cable to POd and PC
 * 4)Turn on POD and while screen is black, press the 'PLay' button on Processing.
 * 5)User should see RTC time set to PC time
 * 6) USer must ensure all Timing PODs times are synced with each other
 * 
 * To Set Stage ID:
 * 1)Put POD in programming mode (dipswitch 2)
 * 2)Turn on POD and while screen is black, scan a card/watch until desired Stage ID is on screen
 * (There are a max of 8 Stages to choose from)
 * (If you do not get to the desired Stage ID before countdown runs out, reset the arduino and carry on scanning)
 * 3)Put POD out of programming mode (dipswitch 2)
 * 4) Turn off/on (or reset) POD and check that desired Stage is showing on the top line of LCD
 * 
 * displays the Time and displays led and start tone once he has scanned his RFID watch.
 * The scan time is  written to the RFID watch for download at a later stage
 * -----------------------------------------------------------------------------------------
updates 4/9/2021
removed battery beep -suspect racers might think that is a succesful scan beep and go for it.
added functionality for ESP-01 to plug in (with code from ESP_NTP_sync_POD.ino) more info here https://www.geekstips.com/arduino-time-sync-ntp-server-esp8266-udp/
and if in Configure mode, it will update RTC time if connected to internet, confirmed by 3 note doBatteryBeep buzzer  

ESP-01 to BOARD connections
Gnd   BT Gnd
3.3   BT VCC (Bit dodgy as this is not 3.3v but could be up to 4.7v)
RX    BT RX (Pin 9)
TX    BT TX (Pin8)
RST   BT EN (VCC)
*/
