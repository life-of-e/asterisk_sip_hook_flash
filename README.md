# asterisk_sip_hook_flash

Tested with Asterisk 13 and Asterisk 16.  Recommended with Asterisk 16.

Modifications to Asterisk PBX to support sending a hook flash (Event 16) to a SIP ATA with an FXO port using RFC2833 or RFC4733 signalling.  Initially created to support a Grandstream HT813 ATA.  May also support Grandstream HT503 and Linksys SPA3102.

I created this simple patch because I needed to handle call waiting on my analog phone line (PSTN) connected to the FXO port of my Grandstream HT813 hybrid adapter.

The HT813 will accept an inband RTP signal (RFC2833 or RFC4733) set to Event 16.  This particular event code was deprecated in the RFCs thus any compliant program is not strictly required to support it however it remains a reserved code in the RFC so that it will not be reassigned later.  As such Asterisk did not have the capability to send this code since it was not a required implementation.

The changes allow the use of the character 'F' or 'f' in the SendDTMF() dialplan application (e.g. SendDTMF(F)) to transmit the hook flash event code.

To use this capability from a phone (especially a SIP phone) all of the following must be true:
1.  The ATA is capable of sending a hook flash to its FXO port
2.  The ATA specifically supports RFC2833 or RFC4733 for receiving events and has documented using either one for receiving a hook flash event
3.  The ATA configuration in sip.conf or pjsip.conf must set dtmfmode=rfc2833 or dtmfmode=rfc4733
4.  A feature code in features.conf must be created to execute SendDTMF(F) and send the packet towards the ATA
    Example:  hookflash => ##,peer,SendDTMF,F
    
 
