LazSerial v0.1 
Serial Port Component for Lazarus (windows and linux).
by Jurassic Pork  03/2013
This library is Free software; you can rediStribute it and/or modify it
  under the terms of the GNU Library General Public License as published by
  the Free Software Foundation; either version 2 of the License, or (at your
  option) any later version.

  This program is diStributed in the hope that it will be useful, but WITHOUT
  ANY WARRANTY; withOut even the implied warranty of MERCHANTABILITY or
  FITNESS FOR A PARTICULAR PURPOSE. See the GNU Library General Public License
  for more details.

  You should have received a Copy of the GNU Library General Public License
  along with This library; if not, Write to the Free Software Foundation,
  Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA. }

 Based on  :
- SdpoSerial v0.1.4
  CopyRight (C) 2006-2010 Paulo Costa
   paco@fe.up.pt
 
- Synaser library  by Lukas Gebauer 
- TcomPort component 


Features :
Changed :  baudrate values.
           stop bits  new value : 1.5
new event : onstatus
new property FRcvLineCRLF : if this property is true, you use RecvString
in place of RecvPacket when you read data from the port.

new procedure  ShowSetupDialog to open a port settings form :
the device combobox contain the enumerated ports.
new procedure to enumerate real serial port on linux ( in synaser).

Demo : a simulator of serial port gps + serial port receiver :
you can send NMEA frames ( GGA GLL RMC) to the opened serial port
(start gps simulator). You can change speed and heading.
In the memo you can see what is received from  the opened serial port.
In the status bar you can see the status events.

tested with windows 7 and Ubuntu 12.04
                                       
if you haven't serial ports in your PC you can use virtual ports :
1 - WINDOWS 
To simulate  a paired serial ports on  windows : com0com   
ex : 

2 - Linux
To simulate  a paired serial ports on linux : socat 
ex :  socat -d -d PTY: PTY:

To connect to a bluetooth GPS on Linux
echo connection to a  bluetooth GPS(/dev/rfcomm0)

sudo rfcomm bind  0 xx:xx:xx:xx:xx:xx 1


Sorry for my poor english but it isn't my natural language.
----------------------------------------------------------------------------------------------------------------

Patch for LazSerial to work with OS-X by rphoover http://forum.lazarus.freepascal.org/index.php?topic=32632.0

Serial Port Component for Lazarus (windows, linux, and OS-X)

Attached is a patch on the latest check-in for LazSerial located on GitHub.  The latest check-in on git-hub was dated Aug 28, 2016 as of this post.  For those interested in using LazSerial with OS-X, the attached patch should get you going on OS-X.

As a part of the patch, a new property was added to the TBlockSerial class in synaser.pas, added as NonBlock.  The NonBlock property is for Unix users (Linux and OS-X included).  When NonBlock is True, the call to the FpOpen method in TBlockSerial.Connect will not block when an of CTS, DSR, or Carrier are not active.
