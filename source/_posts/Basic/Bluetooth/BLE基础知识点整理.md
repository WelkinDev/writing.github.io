---
title: BLE基础知识点整理
date: 2021-10-19 21:27:22
tags:
---




## Content

[oreilly](https://learning.oreilly.com/library/view/building-bluetooth-low/9781786461087/3323a094-8c3b-4c99-b28a-b284745a61b5.xhtml)
```
Attribute Protocol (ATT) and Generic Attribute Profile (GATT)

Bluetooth Low Energy brought two core specifications and every Low Energy profile is supposed to use them. Attribute Protocol and Generic Attribute Profile.

Attribute Protocol is a low-level layer that defines how to transfer data. It identifies the device discovery, reading and writing attributes on a fellow device. On the other hand, Generic Attribute Profile is built on the top of ATT to give high-level services to the manufacturer implementing LE. These services are basically used to manage the data transfer process in a more systematic way. For example, GATT defines if a device's role is going to be Server or Client.

An interesting thing about ATT and GATT is that they are not transport-layer specifications, that means that they can be implemented on BR/EDR or LE. GATT is a mandatory entity in LE and used to discover services and characteristics. The GATT server listens to an ATT requests and confirmations sent by GATT client. GATT server stores, process and transfer the data to the client. Another role of the GATT is that it defines the data arrangement on the server side so that the client can read it accordingly. The data transfer between GATT server and GATT client is called an "Attribute". An attribute is uniquely identified by a Universally Unique Identifier (UUID) which is 128 bits long string ID.

The Bluetooth system consists of four base layers. Radio (Physical layer), Baseband, Link Layer, and L2CAP.
More information about the working on these layers can be found in the core specification document: https://www.bluetooth.com/specifications/adopted-specifications.
```


## Record
**BLE 5.2 Doc:**
Vol 1, Part A, 1.4 NOMENCLATURE （Page: 196)

## Reference 
[Smart Bluetooth: GATT Vs. ATT - what are the differences between them?](https://stackoverflow.com/questions/28793182/smart-bluetooth-gatt-vs-att-what-are-the-differences-between-them/28799589)

[Generic Attribute Profile (GATT)](https://www.carrentalgateway.com/glossary/generic-attribute-profile/)

[Bluetooth Low-Energy 5.0 Throughput Testing](https://www.engeniustech.com/technical-papers/bluetooth-low-energy.pdf)

[iOS MTU size why only 185 bytes](https://devzone.nordicsemi.com/f/nordic-q-a/44825/ios-mtu-size-why-only-185-bytes)

[Negotiate BLE MTU on iOS](https://stackoverflow.com/questions/41977767/negotiate-ble-mtu-on-ios/42336001#42336001)

// Apple 
[maximumWriteValueLengthForType:](https://developer.apple.com/documentation/corebluetooth/cbperipheral/1620312-maximumwritevaluelengthfortype)
[CBCharacteristicWriteType](https://developer.apple.com/documentation/corebluetooth/cbcharacteristicwritetype)

// Bluetooth Specification
[Core Specification 4.0](https://www.bluetooth.com/specifications/specs/core-specification-4-0/)
[Core Specification 4.2](https://www.bluetooth.com/specifications/specs/core-specification-4-2/)
[Bluetooth Core Specification Version 5.0 Feature Overview](https://www.bluetooth.com/bluetooth-resources/bluetooth-5-go-faster-go-further/)
[Core Specification 5.3](https://www.bluetooth.com/specifications/specs/core-specification/)
