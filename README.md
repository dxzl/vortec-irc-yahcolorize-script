# vortec-irc-yahcolorize-script
IRC chat-client script that allows Vortec to communicate with YahCoLoRiZe

You can remotely change the YahCoLoRiZe chat-room (channel) and process text directly by adding some Aliases to Vortec.

In Vortec, click the Aliases tab then the +. Enter the name CCHAN and click OK. Paste in this line:

```
/ddepoke colorize command ddechan *1
```

Hit + again, enter CPLAY and click OK. Paste in this line:

```
/ddeplay colorize command ddeplay *1
```

Hit + again, enter CX and click OK. Paste in this line:

```
/ddepoke colorize command ddevtext *1
```

Now you can change the chat-room with /CCHAN #new-room, and send color-text with /CX my-line of chat text. You can also now use /CPLAY start|stop|pause|resume and /CPLAY <path of a text file>

If you are adventurous, instead of the above alias for CX, use this: /runscript [colorize] $activewin *1. To add the script that goes with this command, click the +, type [COLORIZE], in braces, and press OK. Paste in the script below and click the ✔ 

```
{
 Script:      [COLORIZE] for YahCoLoRiZe
 Author:      dxzl@live.com
 File:        colorize.ops
 Version:     7.0
 Vortec:      0.4.13 or higher
 YahCoLoRiZe: 5.70 or higher
 Usage:       Create alias CX: /runscript [colorize] $activewin *1
              Then in a chat window you type: /cx sometext

 This script is called by the CX alias. It sends text to YahCoLoRiZe
 where it is processed and returned to your chat-window :-)
}
var Wind,Parms: string;
begin
  Wind := $1; Parms := *2;
  Command('/ddepoke colorize command ddechan '+Wind);
  Command('/ddepoke colorize command ddeplay '+Wind);
  Command('/ddepoke colorize command ddevtext '+Parms);
end;
```

As an alternative to pasting-in the script, Vortec lets you install it
using colorize.oop (included in the master GitHub zip)

For additional info: http://www.yahcolorize.com/#Vortec
