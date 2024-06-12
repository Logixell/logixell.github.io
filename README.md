<html xmlns:o="urn:schemas-microsoft-com:office:office"
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"
xmlns="http://www.w3.org/TR/REC-html40">

<head>

<meta name=ProgId content=OneNote.File>
<meta name=Generator content="Microsoft OneNote 15">
</head>

<body lang=en-CA style='font-family:Calibri;font-size:11.0pt'>
<!--StartFragment-->

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>Acronyms</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>MD : Main
Device (Master)</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>SD<span
style='mso-spacerun:yes'>   </span>: Secondary Device (Slave)</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>SPE :
Single Pair Ethernet</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>Overview</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>EtherChain
is a Ultra-low latency point to multipoint communication protocol.<span
style='mso-spacerun:yes'>  </span>It is used to setup a full duplex Virtual
Communications channel from the MD to all the SD devices over one Single Pair
Ethernet (SPE) cable.<span style='mso-spacerun:yes'>  </span>The SD (Secondary
Device) devices are connected to the MD (Main Device) in a daisy chain
configuration.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Low cost
is the driving factor of EtherChain.<span style='mso-spacerun:yes'> 
</span>This includes component cost,<span style='mso-spacerun:yes'>  </span>CPU
Processing power, Power Consumption and complexity.<span
style='mso-spacerun:yes'>  </span>Labor is typically the highest cost in a
system.<span style='mso-spacerun:yes'>  </span>If the system is so complex that
only few people can understand it then the system cost goes up
dramatically.<span style='mso-spacerun:yes'>  </span>Therefore simplicity must
be considered before adding features that increase complexity.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>Target Application</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>EtherChain
has been designed for multiple axis machine control such as 3D printers and
robot arms.<span style='mso-spacerun:yes'>  </span>These types of machines
require synchronous control of multiple motors.<span style='mso-spacerun:yes'> 
</span>Any network delay in these type of machines would cause motion
error.<span style='mso-spacerun:yes'>  </span>EtherChain subDevices are time
synchronized to the mainDevice to be able to transfer Step and Direction pulses
for stepper motors or servos with minimal delay and skew.<span
style='mso-spacerun:yes'>  </span>In order to minimize frame overhead, the
traditional ethernet frame header has been removed with the exception of the
Frame Check Sequence (FCS) for error detection.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>Phy Interfaces</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>EtherChain
protocol supports Single Pair Ethernet (SPE) 100BaseT1 and 10BaseT1L phy
interfaces.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>100BaseT1
chain link length 15meters</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>10BaseT1L
chain link length 2000meters</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Based on
EtherCat type daisy chain cut through data.<span style='mso-spacerun:yes'> 
</span>Data looped back at end of chain.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>EtherChain vs Ethernet</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>The
difference between standard Ethernet and EtherChain is that Ethernet
connections are made in a point to point star connection and require a switch
or router.<span style='mso-spacerun:yes'>  </span>EtherChain on the other hand
is connected in a Daisy Chain fashion and does not require any switch.<span
style='mso-spacerun:yes'>  </span>One chain consists of one MD connected to
multiple SD's.<span style='mso-spacerun:yes'>  </span>Direct communication
between SD's is not possible. </p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>EthterChain vs EtherCat</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>EtherChain
is a very low latency Protocol similar to EtherCat used in industrial settings
but without the burden of being backwards compatible with other industrial
protocols.<span style='mso-spacerun:yes'>  </span>This allows for an
inexpensive lightweight and easy to understand interface.<span
style='mso-spacerun:yes'>  </span>Unlike EtherCat, EtherChain does not support
3 port devices for network branching.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>Single Pair Ethernet</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Since the
SPE interface requires a bridge to connect to a standard Ethernet network, the
Ethernet header can be removed from the SPE network to save bandwidth.<span
style='mso-spacerun:yes'>  </span>An EtherChain packet will go to every node
thus making the use of MAC addresses unnecessary.<span
style='mso-spacerun:yes'>  </span>The EtherChain can be connected to an
Ethernet network though a bridge protocol on the master device which translates
the data into standard Ethernet packets.<span style='mso-spacerun:yes'> 
</span>However care must be taken that all time critical data is processed in
the Master device in order to maintain the key benefit of EtherChain which is
time synchronization.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Supports
Distributed Clock for synchronizing all the slaves to the master clock.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>OSI runs
at the physical layer.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>EtherCat
State machine: Init, Pre-Op, Safe-op, operational, (bootstrap for upgrades)</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>ESC:
Ethercat Slave Controller</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Master=mainDevice</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Slave=SecondaryDevice
</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US><span
style='mso-spacerun:yes'> </span></p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Packet
Type</p>

<div style='direction:ltr'>


Packet   Type   Number | Description
-- | --
0 | IDLE   packet
1 | INIT   packet
  |  
  |  
  |  
  |  
  |  
  |  



</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Runs on
IEEE 802.3bw (BroadR-Reach) PHY</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Based on
EtherCat type daisy chain cut through data.<span style='mso-spacerun:yes'> 
</span>Data looped back at end of chain.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Etherchain
frame:</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>7 bytes
Start of Frame: 10101010</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
Start of Frame Delimiter: 10101011</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
Packet type</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
packet sequence number (rollover) used for detecting lost packets</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
hop number (gets incremented every time the packet is retransmitted to the next
level)</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'
lang=en-US>1 byte broadcast datagram length</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'
lang=en-US>X bytes broadcast datagram</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'
lang=en-US>1 byte hop X datagram length</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'
lang=en-US>Y bytes of hop X datagram</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>…</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>4 bytes
CRC/FCS frame check</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>12 bytes
Interframe Gap</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h3 style='margin:0in;font-family:Calibri;font-size:12.0pt;color:#5B9BD5'
lang=en-US>0 IDLE packet type</h3>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>This
packet does not contain any datagrams.<span style='mso-spacerun:yes'> 
</span>When a SD receives this packet it must immediately go to IDLE
state.<span style='mso-spacerun:yes'>  </span>This is used to determine the
number of hops in the loop.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h3 style='margin:0in;font-family:Calibri;font-size:12.0pt;color:#5B9BD5'
lang=en-US>1 INIT packet type</h3>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>This
packet contains the same datagram format as the Run packet type except that it
is only used for reading and writing initialization registers.<span
style='mso-spacerun:yes'>  </span>255 bytes of data which are all set to 0 by
the master.<span style='mso-spacerun:yes'>  </span>The slaves will then insert
their subDevice ID number into the appropriate byte which corresponds to the
hop number.<span style='mso-spacerun:yes'>  </span>If a slave does not have an
ID assigned yet it will insert 0.<span style='mso-spacerun:yes'>  </span>The
master must then assign it a proper number.<span style='mso-spacerun:yes'> 
</span>Once the master receives a packet with all the proper ID's it can go to
the next state.<span style='mso-spacerun:yes'>  </span>The slave will take note
of its hop number and respond to that hop.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Format:</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
Number of Hops detected by the previous poll</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h3 style='margin:0in;font-family:Calibri;font-size:12.0pt;color:#5B9BD5'
lang=en-US>2 RUN packet type</h3>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>This
packet is used to communicate with individual subDevices.<span
style='mso-spacerun:yes'>  </span>It is like a virtual COM port to each
subDevice.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Format:</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte SD
interrupt register</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>2 bytes
registers</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
COM length<span style='mso-spacerun:yes'>  </span>//of hop 1</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 to 255
bytes data</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>2 bytes
registers</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 byte
COM length //of hop 2</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>1 to 255
bytes data</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>…</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>Interrupt
Register</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>4
Interrupt bits (MD writing to these bits will clear them)</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>4 bits
COM request (Request next data packet size X 4)</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>subDevice
bandwidth request.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>When a
subDevice has data to send to the master it will buffer the data in a fifo and
enter the fill level into the appropriate Hop Length field so that the
MainDevice will increase the HopLength in the next frame.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>If the
mainDevice detects an unexpected hop number it immediately switches back to
init state and all subDevices go into init mode.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>&nbsp;</p>

<h2 style='margin:0in;font-family:Calibri;font-size:14.0pt;color:#2E75B5'
lang=en-US>3 Loopback packet type</h2>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt' lang=en-US>This
packet type indicated that it has been looped back by an open port on the last
SD device on the chain.<span style='mso-spacerun:yes'>  </span>The FCS will
have been recalculated and will not be monitored or altered by the other SD
devices in the chain.<span style='mso-spacerun:yes'>  </span>If a master port
encounters this type of packet it will automatically switch ports.</p>

<!--EndFragment-->
</body>

</html>

