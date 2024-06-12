EtherChain.net protocol

Acronyms
MD : Main Device (Master)
SD   : Secondary Device (Slave)
SPE : Single Pair Ethernet

Overview
EtherChain is a Ultra-low latency point to multipoint communication protocol.  It is used to setup a full duplex Virtual Communications channel from the MD to all the SD devices over one Single Pair Ethernet (SPE) cable.  The SD (Secondary Device) devices are connected to the MD (Main Device) in a daisy chain configuration.

Low cost is the driving factor of EtherChain.  This includes component cost,  CPU Processing power, Power Consumption and complexity.  Labor is typically the highest cost in a system.  If the system is so complex that only few people can understand it then the system cost goes up dramatically.  Therefore simplicity must be considered before adding features that increase complexity.

Target Application
EtherChain has been designed for multiple axis machine control such as 3D printers and robot arms.  These types of machines require synchronous control of multiple motors.  Any network delay in these type of machines would cause motion error.  EtherChain subDevices are time synchronized to the mainDevice to be able to transfer Step and Direction pulses for stepper motors or servos with minimal delay and skew.  In order to minimize frame overhead, the traditional ethernet frame header has been removed with the exception of the Frame Check Sequence (FCS) for error detection.

Phy Interfaces
EtherChain protocol supports Single Pair Ethernet (SPE) 100BaseT1 and 10BaseT1L phy interfaces.
100BaseT1 chain link length 15meters
10BaseT1L chain link length 2000meters
Based on EtherCat type daisy chain cut through data.  Data looped back at end of chain.

Serial over EtherChain
I2C is a common interface for sensors and peripherals.  However, the distance of this interface is limited.  This may not be possible due to the short turnaround times required for I2C reads.

EtherChain vs Ethernet
The difference between standard Ethernet and EtherChain is that Ethernet connections are made in a point to point star connection and require a switch or router.  EtherChain on the other hand is connected in a Daisy Chain fashion and does not require any switch.  One chain consists of one MD connected to multiple SD's.  Direct communication between SD's is not possible. 

EthterChain vs EtherCat
EtherChain is a very low latency Protocol similar to EtherCat used in industrial settings but without the burden of being backwards compatible with other industrial protocols.  This allows for an inexpensive lightweight and easy to understand interface.  Unlike EtherCat, EtherChain does not support 3 port devices for network branching.

Single Pair Ethernet
Since the SPE interface requires a bridge to connect to a standard Ethernet network, the Ethernet header can be removed from the SPE network to save bandwidth.  An EtherChain packet will go to every node thus making the use of MAC addresses unnecessary.  The EtherChain can be connected to an Ethernet network though a bridge protocol on the master device which translates the data into standard Ethernet packets.  However care must be taken that all time critical data is processed in the Master device in order to maintain the key benefit of EtherChain which is time synchronization.

Supports Distributed Clock for synchronizing all the slaves to the master clock.

OSI runs at the physical layer.

EtherCat State machine: Init, Pre-Op, Safe-op, operational, (bootstrap for upgrades)

ESC: Ethercat Slave Controller
Master=mainDevice
Slave=SecondaryDevice 
 
Packet Type
Packet Type	Description
Number
0	IDLE packet
1	INIT packet
	
	
	
	
	
	



Runs on IEEE 802.3bw (BroadR-Reach) PHY
Based on EtherCat type daisy chain cut through data.  Data looped back at end of chain.

Etherchain frame:
7 bytes Start of Frame: 10101010
1 byte Start of Frame Delimiter: 10101011
1 byte Packet type
1 byte packet sequence number (rollover) used for detecting lost packets
1 byte hop number (gets incremented every time the packet is retransmitted to the next level)
	2 bytes datagram address
	1 byte  MD datagram length
	1 byte  MD write length
	1 byte    SD write length
	Y bytes of hop X datagram
…
4 bytes CRC/FCS frame check
12 bytes Interframe Gap


Datagram
1 byte type

Type 01 datagram Write to register
  1 byte address
  X bytes data (address increments)

Type 02 datagram write to comm fifo

0 IDLE packet type
This packet does not contain any datagrams.  When a SD receives this packet it must immediately go to IDLE state.  This is used to determine the number of hops in the loop.

1 INIT packet type
This packet contains the same datagram format as the Run packet type except that it is only used for reading and writing initialization registers.  255 bytes of data which are all set to 0 by the master.  The slaves will then insert their subDevice ID number into the appropriate byte which corresponds to the hop number.  If a slave does not have an ID assigned yet it will insert 0.  The master must then assign it a proper number.  Once the master receives a packet with all the proper ID's it can go to the next state.  The slave will take note of its hop number and respond to that hop.
Format:
1 byte Number of Hops detected by the previous poll

2 RUN packet type
This packet is used to communicate with individual subDevices.  It is like a virtual COM port to each subDevice.
Format:
1 byte SD interrupt register
2 bytes registers
1 byte COM length  //of hop 1
1 to 255 bytes data

2 bytes registers
1 byte COM length //of hop 2
1 to 255 bytes data
…

Interrupt Register
4 Interrupt bits (MD writing to these bits will clear them)
4 bits COM request (Request next data packet size X 4)

subDevice bandwidth request.
When a subDevice has data to send to the master it will buffer the data in a fifo and enter the fill level into the appropriate Hop Length field so that the MainDevice will increase the HopLength in the next frame.

SD write request
The Read length is the amount of data in the slave fifo.  If this is larger than the write length then the amount of data sent is equal to the write length.  The master will then subtract the read length from the write length and if there is a remainder (negative) it will increase the datagram size by that amount on the next frame.

If the mainDevice detects an unexpected hop number it immediately switches back to init state and all subDevices go into init mode.

3 Loopback packet type
This packet type indicated that it has been looped back by an open port on the last SD device on the chain.  The FCS will have been recalculated and will not be monitored or altered by the other SD devices in the chain.  If a master port encounters this type of packet it will automatically switch ports.

