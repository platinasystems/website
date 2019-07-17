


# PCC APIs

## Endpoint summary

<table>
  <tr>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>/role</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/site</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/node</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/kubernetes</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/provision</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/templates</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/topology</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/ws</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/cluster</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/hardware-inventory</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/connectivity</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>/interface</td>
    <td></td>
    <td></td>
  </tr>
</table>


## Hardware Inventory

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Add inventory</td>
    <td>/hardware-inventory</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Discovery nodes</td>
    <td>/hardware-inventory/discovery</td>
    <td>GET</td>
    <td></td>
  </tr>
</table>


### Add inventory

Add an inventory to DB.

#### Request
```JSONasPython
{
    "bus": {
        "bmc": {
            "businfo": "pci@0000:00:1f.3",
            "ipcfg": {
                "gateway-hwaddr": "10:0e:7e:fd:ec:88",
                "gateway-ipaddr": "192.168.101.2",
                "hwaddr": "0c:c4:7a:36:b8:2f",
                "ipaddress": "192.168.101.224",
                "netmask": "255.255.255.0",
                "source": "ipmi"
            },
            "name": "bmc",
            "product": "C600/X79 series chipset SMBus Host Controller",
            "type": "bmc",
            "users": [
                {
                    "id": "2",
                    "ipmirole": "Unknown (0x00)",
                    "username": "ADMIN"
                },
                {
                    "id": "3",
                    "ipmirole": "Unknown (0x00)",
                    "username": "readonly"
                },
                {
                    "id": "4",
                    "ipmirole": "Unknown (0x00)",
                    "username": "root"
                },
                {
                    "id": "5",
                    "ipmirole": "ADMINISTRATOR",
                    "username": "test"
                }
            ],
            "vendor": "Intel Corporation"
        }
    },
    "memory": {
        "DMI:002E": {
            "description": "DIMM DDR3 1333 MHz (0.8 ns)",
            "name": "DMI:002E",
            "size": {
                "unit": "bytes",
                "value": "4294967296"
            },
            "type": "memory"
        },
        "DMI:0030": {
            "description": "DIMM DDR3 1333 MHz (0.8 ns)",
            "name": "DMI:0030",
            "size": {
                "unit": "bytes",
                "value": "4294967296"
            },
            "type": "memory"
        },
        "DMI:0038": {
            "description": "DIMM DDR3 1333 MHz (0.8 ns)",
            "name": "DMI:0038",
            "size": {
                "unit": "bytes",
                "value": "4294967296"
            },
            "type": "memory"
        },
        "DMI:003A": {
            "description": "DIMM DDR3 1333 MHz (0.8 ns)",
            "name": "DMI:003A",
            "size": {
                "unit": "bytes",
                "value": "4294967296"
            },
            "type": "memory"
        }
    },
    "network": {
        "eth0": {
            "businfo": "pci@0000:05:00.0",
            "description": "Ethernet interface",
            "driver": "igb",
            "hwaddr": "0c:c4:7a:33:7a:c6",
            "link": "yes",
            "name": "eth0",
            "peer": {
                "discover-method": "lldp",
                "mgmt-ip": "192.168.101.224",
                "mgmt-mac": "0c:c4:7a:36:b8:2f",
                "peername": "eth0",
                "sysname": "(none).(none)"
            },
            "product": "I350 Gigabit Network Connection",
            "size": "1000000000 bit/s",
            "speed": "1Gbit/s",
            "type": "network",
            "vendor": "Intel Corporation"
        },
        "eth1": {
            "businfo": "pci@0000:05:00.1",
            "description": "Ethernet interface",
            "driver": "igb",
            "hwaddr": "0c:c4:7a:33:7a:c7",
            "link": "no",
            "name": "eth1",
            "product": "I350 Gigabit Network Connection",
            "type": "network",
            "vendor": "Intel Corporation"
        },
        "eth2": {
            "businfo": "pci@0000:82:00.0",
            "description": "Ethernet interface",
            "driver": "mlx5_core",
            "hwaddr": "ec:0d:9a:92:b2:4e",
            "link": "yes",
            "name": "eth2",
            "peer": {
                "discover-method": "lldp",
                "mgmt-ip": "192.168.101.142",
                "mgmt-mac": "6c:ec:5a:07:cb:db",
                "peermac": "6c:ec:5a:07:cb:fd",
                "peername": "xeth32",
                "sysname": "invader22.platinasystems.com"
            },
            "product": "MT27800 Family [ConnectX-5]",
            "type": "network",
            "vendor": "Mellanox Technologies"
        }
    },
    "processor": {
        "cpu:0": {
            "cores": "6",
            "name": "cpu:0",
            "product": "Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz",
            "size": {
                "unit": "Hz",
                "value": "2065724000"
            },
            "type": "cpu"
        },
        "cpu:1": {
            "cores": "6",
            "name": "cpu:1",
            "product": "Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz",
            "size": {
                "unit": "Hz",
                "value": "2040483000"
            },
            "type": "cpu"
        }
    },
    "storage": {
        "storage-PCI:0000:00:1f.2": {
            "block-devices": [
                {
                    "sda": {
                        "model": "WDC WD10EZRZ-00H",
                        "name": "sda",
                        "size": "1953525168",
                        "vendor": "ATA     ",
                        "wwid": "t10.ATA_____WDC_WD10EZRZ-00HTKB0_________________________WD-WCC4J7YHE4Z5"
                    }
                }
            ],
            "businfo": "pci@0000:00:1f.2",
            "driver": "ahci",
            "name": "storage-PCI:0000:00:1f.2",
            "product": "C600/X79 series chipset 6-Port SATA AHCI Controller",
            "type": "storage",
            "vendor": "Intel Corporation"
        },
        "storage-PCI:0000:04:00.0": {
            "businfo": "pci@0000:04:00.0",
            "driver": "isci",
            "name": "storage-PCI:0000:04:00.0",
            "product": "C602 chipset 4-Port SATA Storage Control Unit",
            "type": "storage",
            "vendor": "Intel Corporation"
        }
    },
    "system": {
        "system": {
            "model": "SYS-6017R-TDLR-BK0-LC019 (To be filled by O.E.M.)",
            "name": "system",
            "serial": "S15792125211186",
            "type": "node",
            "uuid": "00000000-0000-0000-0000-0CC47A337AC6",
            "vendor": "Supermicro"
        }
    },
    "version": "1.0",
   "createNode": true
}
```

NOTE: if **createNode** is true the inventory will add the node. The default value is true

### Discovery nodes

List of discovered nodes not yet added.

#### Response
```JSONasPython
{
  "StatusCode": 200,
  "Message": "",
  "MessageType": "OK",
  "Data": [
	{
  	"ID": 1,
  	"nodeId": 0,
  	"MemorySize": 17179869184,
  	"MemorySizeUnit": "bytes",
  	"StorageSize": 0,
  	"StorageSizeUnit": "",
  	"CPUNumber": 2,
  	"CPUCoreNumber": 12,
  	"CPUFrequency": 2040483000,
  	"CPUFrequencyUnit": "Hz",
  	"Bus": {
    	"Bmc": {
      	"Businfo": "pci@0000:00:1f.3",
      	"Ipcfg": {
        	"gateway-hwaddr": "10:0e:7e:fd:ec:88",
        	"gateway-ipaddr": "192.168.101.2",
        	"hwaddr": "0c:c4:7a:36:b8:2f",
        	"ipaddress": "192.168.101.224",
        	"netmask": "255.255.255.0",
        	"source": "ipmi"
      	},
      	"name": "bmc",
      	"product": "C600/X79 series chipset SMBus Host Controller",
      	"type": "bmc",
      	"Users": [
        	{
          	"id": "2",
          	"ipmirole": "Unknown (0x00)",
          	"username": "ADMIN"
        	},
        	{
          	"id": "3",
          	"ipmirole": "Unknown (0x00)",
          	"username": "readonly"
        	},
        	{
          	"id": "4",
          	"ipmirole": "Unknown (0x00)",
          	"username": "root"
        	},
        	{
          	"id": "5",
          	"ipmirole": "ADMINISTRATOR",
          	"username": "test"
        	}
      	],
      	"vendor": "Intel Corporation"
    	}
  	},
  	"Memory": {
    	"DMI:002E": {
      	"description": "DIMM DDR3 1333 MHz (0.8 ns)",
      	"name": "DMI:002E",
      	"type": "memory",
      	"size": {
        	"unit": "bytes",
        	"value": "4294967296"
      	}
    	},
    	"DMI:0030": {
      	"description": "DIMM DDR3 1333 MHz (0.8 ns)",
      	"name": "DMI:0030",
      	"type": "memory",
      	"size": {
        	"unit": "bytes",
        	"value": "4294967296"
      	}
    	},
    	"DMI:0038": {
      	"description": "DIMM DDR3 1333 MHz (0.8 ns)",
      	"name": "DMI:0038",
      	"type": "memory",
      	"size": {
        	"unit": "bytes",
        	"value": "4294967296"
      	}
    	},
    	"DMI:003A": {
      	"description": "DIMM DDR3 1333 MHz (0.8 ns)",
      	"name": "DMI:003A",
      	"type": "memory",
      	"size": {
        	"unit": "bytes",
        	"value": "4294967296"
      	}
    	}
  	},
  	"Network": {
    	"eth0": {
      	"description": "Ethernet interface",
      	"driver": "igb",
      	"hwaddr": "0c:c4:7a:33:7a:c6",
      	"link": "yes",
      	"name": "eth0",
      	"peer": {
        	"discover-method": "lldp",
        	"mgmt-ip": "192.168.101.224",
        	"mgmt-mac": "0c:c4:7a:36:b8:2f",
        	"peername": "eth0",
        	"sysname": "(none).(none)"
      	}
    	},
    	"eth1": {
      	"description": "Ethernet interface",
      	"driver": "igb",
      	"hwaddr": "0c:c4:7a:33:7a:c7",
      	"link": "no",
      	"name": "eth1",
      	"peer": {
        	"discover-method": "",
        	"mgmt-ip": "",
        	"mgmt-mac": "",
        	"peername": "",
        	"sysname": ""
      	}
    	},
    	"eth2": {
      	"description": "Ethernet interface",
      	"driver": "mlx5_core",
      	"hwaddr": "ec:0d:9a:92:b2:4e",
      	"link": "yes",
      	"name": "eth2",
      	"peer": {
        	"discover-method": "lldp",
        	"mgmt-ip": "192.168.101.142",
        	"mgmt-mac": "6c:ec:5a:07:cb:db",
        	"peername": "xeth32",
        	"sysname": "invader22.platinasystems.com"
      	}
    	}
  	},
  	"Processor": {
    	"cpu:0": {
      	"cores": "6",
      	"name": "cpu:0",
      	"product": "Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz",
      	"Size": {
        	"unit": "Hz",
        	"value": "2065724000"
      	},
      	"type": "cpu"
    	},
    	"cpu:1": {
      	"cores": "6",
      	"name": "cpu:1",
      	"product": "Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz",
      	"Size": {
        	"unit": "Hz",
        	"value": "2040483000"
      	},
      	"type": "cpu"
    	}
  	},
  	"Storage": {
    	"storage-PCI:0000:00:1f.2": {
      	"block-devices": [
        	{
          	"sda": {
            	"model": "WDC WD10EZRZ-00H",
            	"name": "sda",
            	"size": "1953525168",
            	"vendor": "ATA 	",
            	"wwid": "t10.ATA_____WDC_WD10EZRZ-00HTKB0_________________________WD-WCC4J7YHE4Z5"
          	}
        	}
      	],
      	"businfo": "pci@0000:00:1f.2",
      	"driver": "ahci",
      	"name": "storage-PCI:0000:00:1f.2",
      	"product": "C600/X79 series chipset 6-Port SATA AHCI Controller",
      	"type": "storage",
      	"vendor": "Intel Corporation"
    	},
    	"storage-PCI:0000:04:00.0": {
      	"block-devices": null,
      	"businfo": "pci@0000:04:00.0",
      	"driver": "isci",
      	"name": "storage-PCI:0000:04:00.0",
      	"product": "C602 chipset 4-Port SATA Storage Control Unit",
      	"type": "storage",
      	"vendor": "Intel Corporation"
    	}
  	},
  	"System": {
    	"system": {
      	"model": "SYS-6017R-TDLR-BK0-LC019 (To be filled by O.E.M.)",
      	"name": "system",
      	"serial": "S15792125211186",
      	"type": "node",
      	"uuid": "00000000-0000-0000-0000-0CC47A337AC6",
      	"vendor": "Supermicro"
    	}
  	},
  	"Version": "1.0"
	}
  ]
}
```


## Node

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Get node</td>
    <td>/node/{id}</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get nodes availability</td>
    <td>/node/availability?status=<status></td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get nodes</td>
    <td>/node</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Add node</td>
    <td>/node</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Update node</td>
    <td>/node</td>
    <td>PUT</td>
    <td></td>
  </tr>
</table>


### Get Node

#### Response
```JSONasPython
{
  "path": "/node/1",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
    "Id": 1,
    "Name": "i60",
    "Host": "172.17.2.60",
    "Type_Id": 0,
    "Iso_Id": 0,
    "Site_Id": null,
    "Kernel_Id": 0,
    "SN": "FDU1857E00023",
    "Model": "model",
    "Vendor": "vendor",
    "KClusterID": 0,
    "CreatedAt": 1559669421209,
    "ModifiedAt": 1559723998302,
    "NodeAuditId": 0,
    "ClusterId": null,
    "owner": 1,
    "bmc": "172.17.3.60",
    "bmcUser": "ADMIN",
    "bmcUsers": [
      "ADMIN"
    ],
    "bmcPassword": "ADMIN",
    "status": "",
    "provisionStatus": "",
    "ready": false,
    "managed": true,
    "tags": [],
    "adminUser": "admin",
    "sshKeys": [],
    "console": "",
    "standby": false,
    "hardwareInventoryId": 0,
    "roles": [
      6,
      7
    ],
    "HardwareInventory": {
      "ID": null,
      "nodeId": 1,
      "MemorySize": 0,
      "MemorySizeUnit": "",
      "StorageSize": 0,
      "StorageSizeUnit": "",
      "CPUNumber": 0,
      "CPUCoreNumber": 0,
      "CPUFrequency": 0,
      "CPUFrequencyUnit": "",
      "Bus": {
        "Bmc": {
          "Businfo": "",
          "Ipcfg": {
            "gateway-hwaddr": "",
            "gateway-ipaddr": "",
            "hwaddr": "",
            "ipaddress": "",
            "netmask": "",
            "source": ""
          },
          "name": "",
          "product": "",
          "type": "",
          "Users": null,
          "vendor": ""
        }
      },
      "Memory": null,
      "Network": null,
      "Processor": null,
      "Storage": null,
      "System": {
        "system": {
          "model": "",
          "name": "",
          "serial": "",
          "type": "",
          "uuid": "",
          "vendor": ""
        }
      },
      "Version": "",
      "createNode": false
    },
    "Apps": [
      {
        "id": "iproute",
        "name": "iproute2",
        "match": true,
        "local": {
          "Installed": true,
          "Version": "default",
          "configurationID": 10
        },
        "remote": {
          "Installed": true,
          "Version": "iproute2-ss140804"
        }
      },
      {
        "id": "maas",
        "name": "Metal as a service",
        "match": true,
        "local": {
          "Installed": true,
          "Version": "default",
          "configurationID": 12
        },
        "remote": {
          "Installed": true,
          "Version": "default"
        }
      }
    ],
    "Roles": null,
    "systemData": {
      "timestamp": 1559724237537,
      "hostname": "",
      "isChanged": false,
      "nodeId": 1,
      "kernel": "Linux 4.13.0-platina-mk1",
      "baseIso": "Debian GNU/Linux 8 (jessie)",
      "serialNumber": "FDU1857E00023",
      "partNumber": "PS-3001-32C-AFA",
      "packages": null,
      "interfaces": null
    },
    "interfaces": [
      {
        "interface": {
          "id": 4,
          "nodeId": 1,
          "name": "docker0",
          "ipv4Addresses": [
            "172.18.0.1"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "02:42:98:73:18:f3",
          "ipv4Subnet": 16,
          "ipv6Subnet": -1,
          "autoneg": false,
          "fecType": "",
          "mediaType": "",
          "speed": "",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 1,
          "nodeId": 1,
          "name": "eth0",
          "ipv4Addresses": [
            "172.17.2.60"
          ],
          "ipv6Addresses": [
            "fe80::5218:4cff:fe00:3069"
          ],
          "defaultGateway": "172.17.2.1",
          "isManagement": true,
          "status": "UP",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:69",
          "ipv4Subnet": 23,
          "ipv6Subnet": 64,
          "autoneg": true,
          "fecType": "",
          "mediaType": "",
          "speed": "1000",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 2,
          "nodeId": 1,
          "name": "eth1",
          "ipv4Addresses": [
            "203.0.113.1"
          ],
          "ipv6Addresses": [
            "fe80::5218:4cff:fe00:306a"
          ],
          "defaultGateway": "",
          "isManagement": false,
          "status": "UP",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:6a",
          "ipv4Subnet": 30,
          "ipv6Subnet": 64,
          "autoneg": true,
          "fecType": "",
          "mediaType": "",
          "speed": "10000",
          "mtu": 9220,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 3,
          "nodeId": 1,
          "name": "eth2",
          "ipv4Addresses": [],
          "ipv6Addresses": [
            "fe80::5218:4cff:fe00:306b"
          ],
          "defaultGateway": "",
          "isManagement": false,
          "status": "UP",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:6b",
          "ipv4Subnet": -1,
          "ipv6Subnet": 64,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "10000",
          "mtu": 9220,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 5,
          "nodeId": 1,
          "name": "eth25",
          "ipv4Addresses": [
            "10.10.10.10"
          ],
          "ipv6Addresses": [
            "fe80::9805:b2ff:fefb:851a"
          ],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "9a:05:b2:fb:85:1a",
          "ipv4Subnet": 24,
          "ipv6Subnet": 64,
          "autoneg": false,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 6,
          "nodeId": 1,
          "name": "xeth1-1",
          "ipv4Addresses": [
            "203.0.113.146",
            "203.0.113.1"
          ],
          "ipv6Addresses": [
            "fe80::5218:4cff:fe00:306c"
          ],
          "defaultGateway": "",
          "isManagement": false,
          "status": "UP",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:6c",
          "ipv4Subnet": 30,
          "ipv6Subnet": 64,
          "autoneg": false,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "10000",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 7,
          "nodeId": 1,
          "name": "xeth1-2",
          "ipv4Addresses": [
            "203.0.113.238",
            "203.0.113.5"
          ],
          "ipv6Addresses": [
            "fe80::5218:4cff:fe00:306d"
          ],
          "defaultGateway": "",
          "isManagement": false,
          "status": "UP",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:6d",
          "ipv4Subnet": 30,
          "ipv6Subnet": 64,
          "autoneg": false,
          "fecType": "",
          "mediaType": "copper",
          "speed": "10000",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 8,
          "nodeId": 1,
          "name": "xeth1-3",
          "ipv4Addresses": [
            "203.0.113.56"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:6e",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "copper",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 9,
          "nodeId": 1,
          "name": "xeth1-4",
          "ipv4Addresses": [
            "203.0.113.150"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:6f",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "copper",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 18,
          "nodeId": 1,
          "name": "xeth10",
          "ipv4Addresses": [
            "203.0.113.6"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:78",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 19,
          "nodeId": 1,
          "name": "xeth11",
          "ipv4Addresses": [
            "203.0.113.90"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:79",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 20,
          "nodeId": 1,
          "name": "xeth12",
          "ipv4Addresses": [
            "203.0.113.192"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:7a",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 21,
          "nodeId": 1,
          "name": "xeth13",
          "ipv4Addresses": [
            "203.0.113.218"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:7b",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 22,
          "nodeId": 1,
          "name": "xeth14",
          "ipv4Addresses": [
            "203.0.113.68"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:7c",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 23,
          "nodeId": 1,
          "name": "xeth15",
          "ipv4Addresses": [
            "203.0.113.202"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:7d",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 24,
          "nodeId": 1,
          "name": "xeth16",
          "ipv4Addresses": [
            "203.0.113.164"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:7e",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 25,
          "nodeId": 1,
          "name": "xeth17",
          "ipv4Addresses": [
            "203.0.113.188"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:7f",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 26,
          "nodeId": 1,
          "name": "xeth18",
          "ipv4Addresses": [
            "203.0.113.38"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:80",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 27,
          "nodeId": 1,
          "name": "xeth19",
          "ipv4Addresses": [
            "203.0.113.74"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:81",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 10,
          "nodeId": 1,
          "name": "xeth2",
          "ipv4Addresses": [
            "203.0.113.34"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:70",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 28,
          "nodeId": 1,
          "name": "xeth20",
          "ipv4Addresses": [
            "203.0.113.110"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:82",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 29,
          "nodeId": 1,
          "name": "xeth21",
          "ipv4Addresses": [
            "203.0.113.170",
            "203.0.113.18"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:83",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": false,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "1000",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 30,
          "nodeId": 1,
          "name": "xeth22",
          "ipv4Addresses": [
            "203.0.113.104"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:84",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 31,
          "nodeId": 1,
          "name": "xeth23",
          "ipv4Addresses": [
            "203.0.113.140"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:85",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 32,
          "nodeId": 1,
          "name": "xeth24",
          "ipv4Addresses": [
            "203.0.113.100"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:86",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 33,
          "nodeId": 1,
          "name": "xeth25",
          "ipv4Addresses": [
            "203.0.113.130"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:87",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 34,
          "nodeId": 1,
          "name": "xeth26",
          "ipv4Addresses": [
            "203.0.113.186"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:88",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 35,
          "nodeId": 1,
          "name": "xeth27",
          "ipv4Addresses": [
            "203.0.113.18"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:89",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 36,
          "nodeId": 1,
          "name": "xeth28",
          "ipv4Addresses": [
            "203.0.113.252"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:8a",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 37,
          "nodeId": 1,
          "name": "xeth29",
          "ipv4Addresses": [
            "203.0.113.196"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:8b",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 11,
          "nodeId": 1,
          "name": "xeth3",
          "ipv4Addresses": [
            "203.0.113.206"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:71",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 38,
          "nodeId": 1,
          "name": "xeth30",
          "ipv4Addresses": [
            "203.0.113.60"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:8c",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 39,
          "nodeId": 1,
          "name": "xeth31",
          "ipv4Addresses": [
            "203.0.113.248"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:8d",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 40,
          "nodeId": 1,
          "name": "xeth32",
          "ipv4Addresses": [
            "203.0.113.124"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:8e",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 12,
          "nodeId": 1,
          "name": "xeth4",
          "ipv4Addresses": [
            "203.0.113.40"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:72",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 13,
          "nodeId": 1,
          "name": "xeth5",
          "ipv4Addresses": [
            "203.0.113.122"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:73",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 14,
          "nodeId": 1,
          "name": "xeth6",
          "ipv4Addresses": [
            "203.0.113.114"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:74",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 15,
          "nodeId": 1,
          "name": "xeth7",
          "ipv4Addresses": [
            "203.0.113.128"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:75",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 16,
          "nodeId": 1,
          "name": "xeth8",
          "ipv4Addresses": [
            "203.0.113.30"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:76",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 17,
          "nodeId": 1,
          "name": "xeth9",
          "ipv4Addresses": [
            "203.0.113.234"
          ],
          "ipv6Addresses": [],
          "defaultGateway": "",
          "isManagement": false,
          "status": "DOWN",
          "adminStatus": "UP",
          "macAddress": "50:18:4c:00:30:77",
          "ipv4Subnet": 31,
          "ipv6Subnet": -1,
          "autoneg": true,
          "fecType": "",
          "mediaType": "fiber",
          "speed": "0",
          "mtu": 1500,
          "remoteLinks": []
        },
        "remoteLinksDetails": []
      },
      {
        "interface": {
          "id": 0,
          "nodeId": 1,
          "name": "aa",
          "ipv4Addresses": [
            "10.20.10.10/32"
          ],
          "ipv6Addresses": null,
          "defaultGateway": "",
          "isManagement": false,
          "status": "",
          "adminStatus": "",
          "macAddress": "",
          "ipv4Subnet": 0,
          "ipv6Subnet": 0,
          "autoneg": false,
          "fecType": "",
          "mediaType": "",
          "speed": "",
          "mtu": 0,
          "remoteLinks": null
        },
        "remoteLinksDetails": null,
        "custom": {
          "nodeID": 1,
          "ifName": "aa",
          "ipv4Address": "10.20.10.10/32",
          "netmask": "",
          "peer": "",
          "gateway": "10.10.10.10",
          "peerID": 0,
          "speed": 100000,
          "dummy": false,
          "ready": false
        }
      },
      {
        "interface": {
          "id": 0,
          "nodeId": 1,
          "name": "adm-interface",
          "ipv4Addresses": [
            "10.10.10.11/32"
          ],
          "ipv6Addresses": null,
          "defaultGateway": "",
          "isManagement": false,
          "status": "",
          "adminStatus": "",
          "macAddress": "",
          "ipv4Subnet": 0,
          "ipv6Subnet": 0,
          "autoneg": false,
          "fecType": "",
          "mediaType": "",
          "speed": "",
          "mtu": 0,
          "remoteLinks": null
        },
        "remoteLinksDetails": null,
        "custom": {
          "nodeID": 1,
          "ifName": "adm-interface",
          "ipv4Address": "10.10.10.11/32",
          "netmask": "",
          "peer": "",
          "gateway": "",
          "peerID": 0,
          "speed": 100000,
          "dummy": false,
          "ready": false
        }
      }
    ]
  }
}
```
**NOTE**: if the ready field is false, the node need to update info, such as bmcPassword.

**NOTE2**: the node has **interfaces**. An interface can be **custom**. In this case it was added by the customer using the endpoint [/interface/](#heading=h.bl9ibyorixnz). If **custom** is not defined the interface was not added by the user. A **custom interface** can be ready. If ready is true the custom interface was already added to node, otherwise it will be add when the node become online/run. **This call returns only non ready custom interfaces** (in addition to already running interfaces).

### Get Nodes

#### Response
```JSONasPython
{
   "StatusCode":200,
   "Message":"",
   "MessageType":"OK",
   "Data":[
  	{
     	"Id":63,
           "ready":true,
     	"Name":"sjc01-pd1-sv01",
     	"Host":"172.17.2.251",
            "Model": "model",
            "Vendor": "vendor",
     	"Type_Id":3,
     	"Iso_Id":4,
     	"Site_Id":3,
     	"Kernel_Id":6,
     	"Validation_status_id":34,
     	"SN":"2",
            "Model": "model",
            "Vendor": "vendor",
     	"KClusterID":0,
     	"CreatedAt":1550018559315,
     	"ModifiedAt":1551318222140,
     	"ExecId":"b5ba2e042e634d29804ca9b837aba2b9",
     	"NodeAuditId":0,
     	"ClusterId":4,
     	"owner":1,
     	"status":"Mismatch",
     	"provisionStatus":"Finished",
     	"hardwareInventoryId":0,
     	"ValidationStatus":{
        	"Id":34,
        	"kernel":"Linux 4.18.0-1.el7.elrepo.x86_64",
        	"IsKernelMatched":true,
        	"BaseISO":"CentOS Linux 7 (Core)",
        	"IsBaseISOMatched":true,
        	"SerialNumber":"S308385X8515925",
        	"IsSNMatched":false,
        	"Type":"SYS-1029TP-DTR",
        	"IsTypeMatched":true,
        	"LldpVersion":"",
        	"IsLldpMatched":true,
        	"EthtoolVersion":"4.8",
        	"IsEthtoolMatched":false,
        	"IprouteVersion":"iproute2-ss170501",
        	"IsIprouteMatched":false,
        	"GoesVersion":"",
        	"IsGoesMatched":true,
        	"FrrVersion":"5.0.1",
        	"IsFrrMatched":false,
        	"OverallStatus":false,
        	"CreatedAt":0,
        	"ModifiedAt":0
     	},
     	"nodeAvailabilityStatus":{
        	"nodeId":63,
        	"updatedAt":1552061669308,
        	"connectionStatus":"offline",
        	"usageStatus":"normal",
        	"cpuUsage":4.2,
        	"memoryUsage":8.7
     	}
  	},
  	{
     	"Id":52,
            “ready”:true,
     	"Name":"sv14",
     	"Host":"172.17.2.114",
     	"Type_Id":0,
     	"Iso_Id":0,
     	"Site_Id":5,
     	"Kernel_Id":0,
     	"Validation_status_id":0,
     	"SN":"",
            "Model": "model",
            "Vendor": "vendor",
     	"KClusterID":0,
     	"CreatedAt":1549943824579,
     	"ModifiedAt":1551318344009,
     	"ExecId":"9e80ad35fe04422fbb44d8bde9077ff2",
     	"NodeAuditId":0,
     	"ClusterId":16,
     	"owner":9,
     	"status":"Match",
     	"provisionStatus":"Failed",
     	"hardwareInventoryId":0,
     	"ValidationStatus":{
        	"Id":0,
        	"kernel":"",
        	"IsKernelMatched":false,
        	"BaseISO":"",
        	"IsBaseISOMatched":false,
        	"SerialNumber":"",
        	"IsSNMatched":false,
        	"Type":"",
        	"IsTypeMatched":false,
        	"LldpVersion":"",
        	"IsLldpMatched":false,
        	"EthtoolVersion":"",
        	"IsEthtoolMatched":false,
        	"IprouteVersion":"",
        	"IsIprouteMatched":false,
        	"GoesVersion":"",
        	"IsGoesMatched":false,
        	"FrrVersion":"",
        	"IsFrrMatched":false,
        	"OverallStatus":false,
        	"CreatedAt":0,
        	"ModifiedAt":0
     	},
     	"nodeAvailabilityStatus":{
        	"nodeId":52,
        	"updatedAt":1550169243934,
        	"connectionStatus":"offline",
        	"usageStatus":"normal",
        	"cpuUsage":0,
        	"memoryUsage":0
     	}
  	},
  	{
     	"Id":84,
           “ready”:true,
     	"Name":"cvb",
     	"Host":"172.17.2.115",
     	"Type_Id":1,
     	"Iso_Id":0,
     	"Site_Id":5,
     	"Kernel_Id":0,
     	"Validation_status_id":0,
     	"SN":"",
            "Model": "model",
            "Vendor": "vendor",
     	"KClusterID":0,
     	"CreatedAt":1550183275239,
     	"ModifiedAt":1552499415913,
     	"ExecId":"5733f258d01c47ee9f5969fcc5467898",
     	"NodeAuditId":0,
     	"ClusterId":16,
     	"owner":9,
     	"status":"Match",
     	"provisionStatus":"Failed",
     	"hardwareInventoryId":0,
     	"ValidationStatus":{
        	"Id":0,
        	"kernel":"",
        	"IsKernelMatched":false,
        	"BaseISO":"",
        	"IsBaseISOMatched":false,
        	"SerialNumber":"",
        	"IsSNMatched":false,
        	"Type":"",
        	"IsTypeMatched":false,
        	"LldpVersion":"",
        	"nodeAvailabilityStatus":{
           	"nodeId":52,
           	"updatedAt":1550169243934,
           	"connectionStatus":"offline",
           	"usageStatus":"normal",
           	"cpuUsage":0,
           	"memoryUsage":0
        	}
     	}
  	}
   ]
}
```

**NOTE**: if the ready field is false, the node need to update info, such as bmcPassword

#### Filter examples

<table>
  <tr>
    <td>Query</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>/node?search=tags:tag2,tag1'</td>
    <td>All nodes which contains the 2 tags</td>
  </tr>
  <tr>
    <td>/node?search=tags:tag1'</td>
    <td>All nodes which contains the "tag1" tag</td>
  </tr>
</table>


### Get Nodes Availability

#### Parameters

<table>
  <tr>
    <td>Parameter</td>
    <td>Values</td>
  </tr>
  <tr>
    <td>status</td>
    <td>"online"  => to get only online nodes
“offline” => to get only offline nodes
“” => to get all statuses</td>
  </tr>
</table>


#### Response
```JSONasPython
{
  "path": "/node/availability?status=online",
  "status": 200,
  "message": "[Node statuses] fetch success",
  "error": "",
  "Data": [
    {
      "nodeId": 4,
      "node": "i43",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 14,
      "node": "i24",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 10,
      "node": "i44",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 38,
      "node": "i36",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 49,
      "node": "sjc01-pd1-sv08",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 24,
      "node": "i27",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 46,
      "node": "sjc01-pd2-sv02",
      "cluster": "",
      "site": "",
      "status": "online"
    },
    {
      "nodeId": 50,
      "node": "sjc01-pd1-sv09",
      "cluster": "",
      "site": "",
      "status": "online"
    }
  ]
}
```


### Add Node
```JSONasPython
{
   "name":"NODE_NAME",
   "host":"10.10.10.5",
   "clusterId":1,
   "kClusterId":1,
   "siteId":1,
   "roleIds":[
  	1,
  	2,
  	3
   ],
   "tags":["tag1","tag2","tag3"],
   "bmc":"10.10.11.5",
   "bmcUser":"osUser1",
   "bmcUsers":["osUser1","osUser2","osUser3"],
   "bmcPassword":"osPassword",
   "bmcKey":"osKey",
   "hwAddr":"00:00:00:00:00:00:00"
}
```

NOTE: optional in brown. bmcPassword and bmcKey can be exclusive

### Update Node
```JSONasPython
{
   "id":5,
   "name":"NODE_NAME",
   "host":"10.10.10.5",
   "clusterId":1,
   "kClusterId":1,
   "siteId":1,
   "roleIds":[
  	1,
  	2,
  	3
   ],
   "tags":["tag1","tag2","tag3"],
   "bmc":"10.10.11.5",
   "bmcUser":"osUser1",
   "bmcUsers":["osUser1","osUser2","osUser3"],
   "bmcPassword":"osPassword",
   "bmcKey":"osKey"
}
```

NOTE: optional in brown. bmcPassword and bmcKey can be exclusive

### Standby Node
```JSONasPython
{
   "id":5,
   "standby":true
}
```

## Topology

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Get topology</td>
    <td>/topology/</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get node topology</td>
    <td>/topology/{nodeid}</td>
    <td>GET</td>
    <td></td>
  </tr>
</table>


### Get topology

#### Response
```JSONasPython
{
   "StatusCode":200,
   "Message":"",
   "MessageType":"OK",
   "Data":[
{
  	"NodeId": 4,
  	"NodeName": "i43",
  	"NodeGroupId": 0,
  	"NodeGroupName": "",
  	"links": [
    	{
      	"ipv4_addresses": [
        	"10.0.7.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd6"
      	],
      	"interface_name": "xeth7",
      	"mac_address": "50:18:4c:00:0b:d6",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.11.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bda"
      	],
      	"interface_name": "xeth11",
      	"mac_address": "50:18:4c:00:0b:da",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.1.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd0"
      	],
      	"interface_name": "xeth1",
      	"mac_address": "50:18:4c:00:0b:d0",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.1.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd0"
      	],
      	"interface_name": "xeth1",
      	"mac_address": "50:18:4c:00:0b:d0",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.1.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd0"
      	],
      	"interface_name": "xeth1",
      	"mac_address": "50:18:4c:00:0b:d0",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.9.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd8"
      	],
      	"interface_name": "xeth9",
      	"mac_address": "50:18:4c:00:0b:d8",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.15.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bde"
      	],
      	"interface_name": "xeth15",
      	"mac_address": "50:18:4c:00:0b:de",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.5.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd4"
      	],
      	"interface_name": "xeth5",
      	"mac_address": "50:18:4c:00:0b:d4",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.13.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bdc"
      	],
      	"interface_name": "xeth13",
      	"mac_address": "50:18:4c:00:0b:dc",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.3.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:bd2"
      	],
      	"interface_name": "xeth3",
      	"mac_address": "50:18:4c:00:0b:d2",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.17.31"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:be0"
      	],
      	"interface_name": "xeth17",
      	"mac_address": "50:18:4c:00:0b:e0",
      	"remote_node_id": 65,
      	"remote_node_name": "i30",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.8.30"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::5218:4cff:fe00:b53"
      	],
      	"remote_interface_name": "xeth8",
      	"remote_mac_address": "50:18:4c:00:0b:53"
    	}
  	]
	},
  	{
     	"NodeId":14,
     	"NodeName":"i30",
     	"NodeGroupId":5,
     	"NodeGroupName":"test",
     	"links":[
        	{
           	"ipv4_addresses":[
              	"192.168.2.2",
              	"192.168.2.3"
           	],
           	"ipv6_addresses":null,
           	"interface_name":"eth1",
           	"mac_address":"00-00-00-00-00-07",
           	"remote_node_id":14,
           	"remote_node_name":"i30",
           	"remote_ipv4_ipv4_addresses":[
              	"192.168.2.4",
              	"192.168.2.5"
           	],
           	"remote_ipv6_ipv4_addresses":null,
           	"remote_interface_name":"eth2",
           	"remote_mac_address":"00-00-00-00-00-08"
        	}
     	]
  	},
  	{
     	"NodeId":17,
     	"NodeName":"i41",
     	"NodeGroupId":5,
     	"NodeGroupName":"test",
     	"links":[
        	{
           	"ipv4_addresses":null,
           	"ipv6_addresses":null,
           	"interface_name":"eth0",
           	"mac_address":"00-00-00-00-00-01",
           	"remote_node_id":14,
           	"remote_node_name":"i30",
           	"remote_ipv4_ipv4_addresses":null,
           	"remote_ipv6_ipv4_addresses":null,
           	"remote_interface_name":"eth2",
           	"remote_mac_address":"00-00-00-00-00-08"
        	},
        	{
           	"ipv4_addresses":[
              	"192.168.1.2",
              	"192.168.1.3"
           	],
           	"ipv6_addresses":null,
           	"interface_name":"eth1",
           	"mac_address":"00-00-00-00-00-02",
           	"remote_node_id":14,
           	"remote_node_name":"i30",
           	"remote_ipv4_ipv4_addresses":[
              	"192.168.1.4",
              	"192.168.1.5"
           	],
           	"remote_ipv6_ipv4_addresses":null,
           	"remote_interface_name":"eth2",
           	"remote_mac_address":"00-00-00-00-00-08"
        	}
     	]
  	}
   ]
}
```

### Get node topology
```JSONasPython
{
  "StatusCode": 200,
  "Message": "",
  "MessageType": "OK",
  "Data": [
	{
  	"NodeId": 24,
  	"NodeName": "i27",
  	"NodeGroupId": 1,
  	"NodeGroupName": "LAX01",
  	"links": [
    	{
      	"ipv4_addresses": [
        	"10.0.35.128"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:1620"
      	],
      	"interface_name": "xeth1-1",
      	"mac_address": "50:18:4c:00:16:20",
      	"remote_node_id": 63,
      	"remote_node_name": "sjc01-pd1-sv01",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.35.129"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::11a0:e4e4:36b0:2b4b"
      	],
      	"remote_interface_name": "enp175s0f1",
      	"remote_mac_address": "90:e2:ba:c6:be:71",
      	"remote_group_name": "LAX01"
    	},
    	{
      	"ipv4_addresses": [
        	"10.0.36.129"
      	],
      	"ipv6_addresses": [
        	"fe80::5218:4cff:fe00:1633"
      	],
      	"interface_name": "xeth11-1",
      	"mac_address": "50:18:4c:00:16:33",
      	"remote_node_id": 47,
      	"remote_node_name": "sjc01-pd1-sv06",
      	"remote_ipv4_ipv4_addresses": [
        	"10.0.36.139"
      	],
      	"remote_ipv6_ipv4_addresses": [
        	"fe80::202:c9ff:fe09:b782"
      	],
      	"remote_interface_name": "enp1s0",
      	"remote_mac_address": "00:02:c9:09:b7:82",
      	"remote_group_name": "LAX01"
    	}
  	]
	}
  ]
}
```

## Provision

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Do Provision</td>
    <td>/provisions/</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Undo Provision</td>
    <td>/provisions/</td>
    <td>POST</td>
    <td></td>
  </tr>
</table>


### Do provision

#### Request
```JSONasPython
{
   "template":{
  	"id":5,
  	"nodes":[
     	25,
     	26,
     	27
  	]
   },
   "clean":false
}
```

**NOTE**: if clean is true delete ALL the old apps

### Undo provision

#### Request
```JSONasPython
{
   "template":{
  	"nodes":[
     	25,
     	26,
     	27
  	]
   },
   "clean":true
}
```

## Template

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Add Template</td>
    <td>/templates/</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Delete</td>
    <td>/templates/{ID}</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Get template</td>
    <td>/templates/{ID}</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get templates</td>
    <td>/templates/</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Update template</td>
    <td>/templates/{ID}</td>
    <td>PUT</td>
    <td></td>
  </tr>
</table>


### Add template

#### Request
```JSONasPython
{
   "name":"my_template_1",
   "description":"my favorite template",
   "configurations":[
  	{
     	"templateID":1,
     	"configurationID":1
  	},
  	{
     	"templateID":2,
     	"configurationID":4
  	}
   ],
   "roles":[
  	1,
  	2,
  	3
   ]
}
```

### Update template

#### Request
```JSONasPython
{
   "name":"my_template_1",
   "description":"my favorite template",
   "configurations":[
  	{
     	"templateID":1,
     	"configurationID":1
  	},
  	{
     	"templateID":2,
     	"configurationID":4
  	}
   ],
   "roles":[
  	1,
  	2,
  	3
   ]
}
```

### Get templates

#### Response
```JSONasPython
{
  "path": "/templates",
  "status": 200,
  "message": "",
  "error": "",
  "Data": [
	{
  	"id": 49,
  	"name": "TEST-FRR-ONLY",
  	"description": "frr only",
  	"configurations": [
    	{
      	"id": 75,
      	"templateID": 49,
      	"configurationID": 1200,
      	"priority": 1
    	}
  	],
  	"roles": [
    	31
  	]
	},
	{
  	"id": 51,
  	"name": "TEST-LLDP-ONLY",
  	"description": "lldp only",
  	"configurations": [
    	{
      	"id": 80,
      	"templateID": 51,
      	"configurationID": 1206,
      	"priority": 1
    	}
  	],
  	"roles": [
    	29
  	]
	},
	{
  	"id": 48,
  	"name": "TEST-GOES-ONLY",
  	"description": "test goes only",
  	"configurations": [
    	{
      	"id": 84,
      	"templateID": 48,
      	"configurationID": 1204,
      	"priority": 1
    	}
  	],
  	"roles": [
    	30,
    	28,
    	31
  	]
	}
  ]
}
```

### Get template

#### Response
```JSONasPython
{
  "path": "/templates/48",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
	"id": 48,
	"name": "TEST-GOES-ONLY",
	"description": "test goes only",
	"configurations": [
  	{
    	"id": 84,
    	"templateID": 48,
    	"configurationID": 1204,
    	"priority": 1
  	}
	],
	"roles": [
  	30,
  	28,
  	31
	]
  }
}
```

## Role

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Add</td>
    <td>/roles/</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Delete</td>
    <td>/roles/{ID}</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Get role</td>
    <td>/roles/{ID}</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get roles</td>
    <td>/roles/</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Update</td>
    <td>/roles/{ID}</td>
    <td>PUT</td>
    <td></td>
  </tr>
</table>


### Add Role

#### Request
```JSONasPython
{
   "name":"NAME",
   "description":"DESCRIPTION",
  "owners":[1,2,3],
   "templateIDs":[
  	1,
  	2,
  	3,
  	4
   ]
}
```

**NOTE**: if owners is [0] the roles will be visible to all tenants

### Update Role

#### Request
```JSONasPython
{
   "name":"NAME",
   "description":"DESCRIPTION",
  "owners":[1,2,3],
   "templateIDs":[
  	1,
  	2,
  	3,
  	4
   ]
}
```

**NOTE**: if owners is [0] the roles will be visible to all tenants

## Cluster

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Add</td>
    <td>/cluster/</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Delete</td>
    <td>/cluster/{ID}</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Update</td>
    <td>/cluster/{ID}</td>
    <td>PUT</td>
    <td></td>
  </tr>
  <tr>
    <td>Get Cluster</td>
    <td>/cluster/{ID}</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get Clusters</td>
    <td>/cluster</td>
    <td>GET</td>
    <td></td>
  </tr>
</table>


### Add Cluster

#### Request
```JSONasPython
{
   "Description":"This is a test",
   "Name":"Test"
}
```

### Update Cluster

#### Request
```JSONasPython
{
   "Description":"This is a test",
   "Name":"Test"
}
```

### Get Cluster

#### Response
```JSONasPython
{
  "path": "/cluster/3",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
	"Id": 3,
	"CreatedAt": 1547118676433,
	"ModifiedAt": 1547118676433,
	"Name": "PROD1",
	"Description": ""
  }
}
```

### Get Clusters

#### Response
```JSONasPython
{
  "path": "/cluster",
  "status": 200,
  "message": "",
  "error": "",
  "Data": [
	{
  	"Id": 3,
  	"CreatedAt": 1547118676433,
  	"ModifiedAt": 1547118676433,
  	"Name": "PROD1",
  	"Description": ""
	{
  	"Id": 4,
  	"CreatedAt": 1547118690404,
  	"ModifiedAt": 1547543381271,
  	"Name": "DEV1",
  	"Description": ""
	},
	{
  	"Id": 29,
  	"CreatedAt": 0,
  	"ModifiedAt": 0,
  	"Name": "yy",
  	"Description": ""
}
 ]
}
```

## Site

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Add</td>
    <td>/site/</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Delete</td>
    <td>/site/{ID}</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Update Site</td>
    <td>/site/{ID}</td>
    <td>PUT</td>
    <td></td>
  </tr>
  <tr>
    <td>Get Site</td>
    <td>/site/{ID}</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get Sites</td>
    <td>/site</td>
    <td>GET</td>
    <td></td>
  </tr>
</table>


### Add Site

#### Request
```JSONasPython
{
"Name": "LAB",
"Description": "TEST"
}
```

### Update Site

#### Request
```JSONasPython
{
"Name": "LAB",
"Description": "TEST"
}
```

### Get Site

#### Response
```JSONasPython
{
  "path": "/site/4",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
	"Id": 4,
	"CreatedAt": 1547118430472,
	"ModifiedAt": 1547118430472,
	"Name": "LAB",
	"Description": ""
  }
}


### Get Sites

#### Response
```JSONasPython
{
  "path": "/site",
  "status": 200,
  "message": "",
  "error": "",
  "Data": [
	{
  	"Id": 1,
  	"CreatedAt": 1547118397473,
  	"ModifiedAt": 1547118397473,
  	"Name": "LAX01",
  	"Description": ""
	},
	{
  	"Id": 2,
  	"CreatedAt": 1547118406104,
  	"ModifiedAt": 1547118406104,
  	"Name": "BOS01",
  	"Description": ""
	},
	{
  	"Id": 3,
  	"CreatedAt": 1547118417902,
  	"ModifiedAt": 1547118417902,
  	"Name": "SJC01",
  	"Description": ""
	},
	{
  	"Id": 23,
  	"CreatedAt": 0,
  	"ModifiedAt": 0,
  	"Name": "test2",
  	"Description": ""
	},
	{
  	"Id": 24,
  	"CreatedAt": 0,
  	"ModifiedAt": 0,
  	"Name": "testSite",
  	"Description": "simple site"
	}
  ]
}
```

## Connectivity

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Get connectivity</td>
    <td>/connectivity/{ID}</td>
    <td>GET</td>
    <td></td>
  </tr>
</table>


### Get Connectivity

#### Response
```JSONasPython
{
  "path": "/connectivity/178",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
	"Id": 178,
	"Name": "i42",
	"Host": "172.17.2.42",
	"Type_Id": 0,
	"Iso_Id": 0,
	"Site_Id": 4,
	"Kernel_Id": 0,
	"SN": "FDU1757C0000D",
	"Model": "",
	"KClusterID": 0,
	"CreatedAt": 1555089781061,
	"ModifiedAt": 1556293900765,
	"NodeAuditId": 0,
	"ClusterId": 6,
	"owner": 1,
	"status": "",
	"provisionStatus": "",
	"ready": false,
	"managed": true,
	"tags": [
  	"RegTestBed2"
	],
	"adminUser": "",
	"sshKeys": [],
	"console": "",
	"hardwareInventoryId": 0,
	"roles": null,
	"HardwareInventory": null,
	"Apps": null,
	"systemData": {
  	"timestamp": 1556611541136,
  	"hostname": "",
  	"isChanged": false,
  	"nodeId": 178,
  	"kernel": "Linux 4.13.0-platina-mk1",
  	"baseIso": "Debian GNU/Linux 9 (stretch)",
  	"serialNumber": "FDU1757C0000D",
  	"partNumber": "PS-3001-32C-AFA",
  	"packages": null,
  	"interfaces": null
	},
	"interfaces": [
  	{
    	"interface": {
      	"id": 155039,
      	"nodeId": 178,
      	"name": "xeth19",
      	"ipv4Addresses": [
        	"10.0.19.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e76"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:76",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155021,
        	"nodeId": 167,
        	"name": "xeth19",
        	"ipv4Addresses": [
          	"10.0.19.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15ae"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:ae",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	},
  	{
    	"interface": {
      	"id": 155028,
      	"nodeId": 178,
      	"name": "xeth29",
      	"ipv4Addresses": [
        	"10.0.29.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e80"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:80",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155026,
        	"nodeId": 167,
        	"name": "xeth29",
        	"ipv4Addresses": [
          	"10.0.29.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15b8"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:b8",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	},
  	{
    	"interface": {
      	"id": 155040,
      	"nodeId": 178,
      	"name": "xeth21",
      	"ipv4Addresses": [
        	"10.0.21.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e78"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:78",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155022,
        	"nodeId": 167,
        	"name": "xeth21",
        	"ipv4Addresses": [
          	"10.0.21.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15b0"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:b0",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	},
  	{
    	"interface": {
      	"id": 155041,
      	"nodeId": 178,
      	"name": "xeth23",
      	"ipv4Addresses": [
        	"10.0.23.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e7a"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:7a",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155023,
        	"nodeId": 167,
        	"name": "xeth23",
        	"ipv4Addresses": [
          	"10.0.23.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15b2"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:b2",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	},
  	{
    	"interface": {
      	"id": 155042,
      	"nodeId": 178,
      	"name": "xeth25",
      	"ipv4Addresses": [
        	"10.0.25.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e7c"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:7c",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155024,
        	"nodeId": 167,
        	"name": "xeth25",
        	"ipv4Addresses": [
          	"10.0.25.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15b4"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:b4",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	},
  	{
    	"interface": {
      	"id": 155029,
      	"nodeId": 178,
      	"name": "xeth31",
      	"ipv4Addresses": [
        	"10.0.31.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e82"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:82",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155027,
        	"nodeId": 167,
        	"name": "xeth31",
        	"ipv4Addresses": [
          	"10.0.31.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15ba"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:ba",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	},
  	{
    	"interface": {
      	"id": 155043,
      	"nodeId": 178,
      	"name": "xeth27",
      	"ipv4Addresses": [
        	"10.0.27.32"
      	],
      	"ipv6Addresses": [
        	"fe80::5218:4cff:fe00:e7e"
      	],
      	"isManagement": false,
      	"status": "UP",
      	"macAddress": "50:18:4c:00:0e:7e",
      	"subnet": "64",
      	"autoneg": false,
      	"fecType": "cl91",
      	"mediaType": "copper",
      	"speed": "100000",
      	"mtu": 1500,
      	"remoteLinks": [
        	{
          	"remoteInterfaceMac": "",
          	"remoteInterfaceName": ""
        	}
      	]
    	},
    	"remoteLinksDetails": [
      	{
        	"id": 155025,
        	"nodeId": 167,
        	"name": "xeth27",
        	"ipv4Addresses": [
          	"10.0.27.29"
        	],
        	"ipv6Addresses": [
          	"fe80::5218:4cff:fe00:15b6"
        	],
        	"isManagement": false,
        	"status": "UP",
        	"macAddress": "50:18:4c:00:15:b6",
        	"subnet": "64",
        	"autoneg": false,
        	"fecType": "cl91",
        	"mediaType": "copper",
        	"speed": "100000",
        	"mtu": 1500,
        	"remoteLinks": null
      	}
    	]
  	}
	]
  }
}
```

## Interface

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Add/Update interface</td>
    <td>/interface</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Delete interface</td>
    <td>/interface</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Enable interface</td>
    <td>/interface/up</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Diasable interface</td>
    <td>/interface/down</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Get custom interfaces</td>
    <td>/interface/custom</td>
    <td>GET</td>
    <td>List of interfaces created by users</td>
  </tr>
  <tr>
    <td>Get all interfaces</td>
    <td>/interface/all/{ID}</td>
    <td>GET</td>
    <td></td>
  </tr>
</table>


### Add Interface

Add an interface to node.

#### Request
```JSONasPython
{
   "nodeID":234,
   "speed":10000,
   "dummy":false,
   "status":”up”,
   "ifName":"eth25",
   "ipv4Address":"10.10.10.10/24, 192.168.1.23/24",  //there could be more than an ip (comma separated)                 “gateway":"10.10.10.1",
   "peer":"test-peer",
   "peerID":90
}
```

### Delete Interface

Delete an inventory from node.

#### Request
```JSONasPython
{
   "nodeID":234,
   "ifName":"eth25"
}
```

### Enable Interface

#### Request
```JSONasPython
{
   "nodeID":234,
   "ifName":"eth25"
}
```

### Disable Interface

#### Request
```JSONasPython
{
   "nodeID":234,
   "ifName":"eth25"
}
```

### Get all interfaces

#### Response
```JSONasPython
{
   "path":"/interface/all/1",
   "status":200,
   "message":"",
   "error":"",
   "Data":[
  	{
     	"id":1,
     	"nodeId":1,
     	"name":"xeth25",
     	"ipv4Addresses":[
        	"10.0.25.32"
     	],
     	"ipv6Addresses":[
        	"fe80::5218:4cff:fe00:e7c"
     	],
     	"isManagement":false,
     	"status":"UP",
     	"adminStatus":"",
     	"macAddress":"50:18:4c:00:0e:7c",
     	"ipv4Subnet":24,
     	"ipv6Subnet":64,
     	"autoneg":false,
     	"fecType":"cl91",
     	"mediaType":"copper",
     	"mtu":1500,
     	"remoteLinks":null,
     	"nodeID":0,
     	"ifName":"",
     	"ipv4Address":"",
     	"netmask":"",
     	"peer":"",
     	"gateway":"",
     	"peerID":0,
     	"dummy":false,
     	"ready":true
  	},
  	{
     	"id":2,
     	"nodeId":1,
     	"name":"xeth26",
     	"ipv4Addresses":[
        	"10.0.26.32"
     	],
     	"ipv6Addresses":[
        	"fe80::5218:4cff:fe00:e7d"
     	],
     	"isManagement":false,
     	"status":"DOWN",
     	"adminStatus":"",
     	"macAddress":"50:18:4c:00:0e:7d",
     	"ipv4Subnet":24,
     	"ipv6Subnet":64,
     	"autoneg":false,
     	"fecType":"cl91",
     	"mediaType":"copper",
     	"mtu":1500,
     	"remoteLinks":null,
     	"nodeID":0,
     	"ifName":"",
     	"ipv4Address":"",
     	"netmask":"",
     	"peer":"",
     	"gateway":"",
     	"peerID":0,
     	"dummy":false,
     	"ready":true
  	},
  	{
     	"id":0,
     	"nodeId":1,
     	"name":"iftest",
     	"ipv4Addresses":[
        	"10.10.10.10"
     	],
     	"ipv6Addresses":null,
     	"isManagement":false,
     	"status":"",
     	"adminStatus":"",
     	"macAddress":"",
     	"ipv4Subnet":0,
     	"ipv6Subnet":0,
     	"autoneg":false,
     	"fecType":"",
     	"mediaType":"",
     	"mtu":0,
     	"remoteLinks":null,
     	"nodeID":1,
     	"ifName":"iftest",
     	"ipv4Address":"10.10.10.10",
     	"netmask":"255.255.255.0",
     	"peer":"",
     	"gateway":"",
     	"peerID":2,
     	"dummy":false,
     	"ready":false
  	}
   ]
}
```

**NOTE**: if ready is false, the interface was added by the customer but is not

##  Kubernetes

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Get kubernetes info</td>
    <td>/kubernetes/info</td>
    <td>GET</td>
    <td>Returns required data for creation/update:<br>
- available versions <br>
- available cni plugins <br>
- available role policies </td>
  </tr>
  <tr>
    <td>Add a new cluster</td>
    <td>/kubernetes</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Get available clusters</td>
    <td>/kubernetes</td>
    <td>GET</td>
    <td>The request support pagination</td>
  </tr>
  <tr>
    <td>Get specific cluster</td>
    <td>/kubernetes/:id</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Update</td>
    <td>/kubernetes/:id</td>
    <td>PUT</td>
    <td></td>
  </tr>
  <tr>
    <td>Remove existing cluster</td>
    <td>/kubernetes/:id</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Deploy application</td>
    <td>/kubernetes/:id/apps</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>Undeploy application</td>
    <td>/kubernetes/:id/apps</td>
    <td>DELETE</td>
    <td></td>
  </tr>
  <tr>
    <td>Upgrade kubernetes cluster version</td>
    <td>/kubernetes/:id/upgrade</td>
    <td>POST</td>
    <td></td>
  </tr>
</table>


### Get Kubernetes Info

Retrieve info about kubernetes from server ( available versions, cluster roles policy ecc )

#### Curl example
```
curl -k -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes/info'</td>
```

#### Response
```JSONasPython
{
  "path": "",
  "status": 200,
  "message": "Kubernetes configuration info",
  "error": "",
  "Data": {
	"versions": [
  	"v1.12.7",
  	"v1.13.5"
	],
	"cniPlugins": [
  	"kube-router"
	],
	"rolePolicies": [
  	{
    	"name": "policy",
    	"cniPlugins": "Masters(M) and workers(W) nodes are chosen randomly and the etcd(E) role is applied to an odd set of these. Specifically if nodes are less then 10 there will be 2M and 3E in total ( 1M and 2W ). If nodes are between 10 and 20 instead 3M and 5E in total ( 2M and 3W ) and so on"
  	},
  	{
    	"name": "custom",
    	"cniPlugins": "Masters(M) and workers(W) nodes and the etcd(E) role are applied as specified by user"
  	}
	]
  }
}
```

### Create cluster

Add a new kubernetes cluster

#### Curl example
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes' -d '{"name":"cluster.test","k8sVersion":"v1.12.7","cniPlugin":"kube-router","nodes":[{"id":1},{"id":2},{"id":3},{"id":4}]}'
```
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes' -d '{"name":"cluster.test","k8sVersion":"v1.12.7","cniPlugin":"kube-router","networkID": 2,"nodes":[{"id":34},{"id":35},{"id":36}]}'
```

#### Request Body

With **auto**policy:
```JSONasPython
{
  "name":"Cluster01",
  "k8sVersion":"1.12.7",
  "cniPlugin":"kube-router",
  "nodes": [
   	 {
  	"id": 1
	},
	{
  	"id": 2
	},
	{
  	"id": 3
	},
	{
  	"id": 4
	},
	{
  	"id": 5
	}
  ]
}
```

With **custom**policy:
```JSONasPython
{
  "name":"Cluster02",
  "rolePolicy":"custom",
  "k8sVersion":"1.12.7",
  "cniPlugin":"kube-router",
  "nodes": [
   	 {
  	"id": 1,
  	"roles": ["master"],
  	"etcd": true
	},
	{
  	"id": 2,
  	"roles": ["master"]
	},
	{
  	"id": 3,
  	"roles": ["worker"],
  	"etcd": false
	},
	{
  	"id": 4,
  	"roles": ["worker"],
  	"etcd": true
	},
	{
  	"id": 10,
  	"roles": ["worker"]  ,
  	"etcd": true
	}
  ]
}
```

#### Response
```JSONasPython
{
  "path": "",
  "status": 200,
  "message": "Cluster with id [12] has been created and it is going to be installed",
  "error": ""
}
```

### Get available clusters

Returns available cluster information

#### Curl example
```
curl -k -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes?page=0&limit=1'
```

#### Request URL [paginated]

**GET**

http://127.0.0.1:8080/kubernetes?page=0&limit=1&search=cni_plugin:kube-router


#### Response

Ansible Parameter

Here latest ansible job executed on cluster is on latestAnsibleJob parameter.

See Ansible section on this guide to check how to sync with ansible job logs at runtime via websocket.

```JSONasPython
{
  "path":"",
  "status":200,
  "message":"",
  "error":"",
  "Data":[
    {
      "ID":1,
      "name":"cluster.test",
      "networkID":1,
      "rolePolicy":"auto",
      "k8sVersion":"v1.12.7",
      "cniPlugin":"kube-router",
      "servicesCIDR":"10.1.0.0/18",
      "podsCIDR":"10.1.64.0/18",
      "deployStatus":"installing",
      "healthStatus":"undefined",
      "latestRestart":null,
      "nodes":[
        {
          "id":1,
          "kclusterID":1,
          "kroles":[
            "master"
          ],
          "Etcd":true,
          "controlIP":"10.0.1.51"
        },
        {
          "id":2,
          "kclusterID":1,
          "kroles":[
            "master"
          ],
          "Etcd":true,
          "controlIP":"10.0.1.52"
        },
        {
          "id":3,
          "kclusterID":1,
          "kroles":[
            "worker"
          ],
          "Etcd":true,
          "controlIP":"10.0.1.53"
        }
      ],
      "apps":[
        {
          "ID":1,
          "kclusterID":1,
          "label":"ES",
          "appName":"elasticsearch",
          "appNamespace":"default",
          "gitUrl":"https://github.com/helm/charts",
          "gitRepoPath":"stable",
          "gitBranch":"master",
          "helmValuesFile":"bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo="
        }
      ],
      "latestAnsibleJob":null
    },
    {
      "ID":2,
      "name":"cluster.test2",
      "networkID":2,
      "rolePolicy":"auto",
      "k8sVersion":"v1.12.7",
      "cniPlugin":"kube-router",
      "servicesCIDR":"10.2.0.0/18",
      "podsCIDR":"10.2.64.0/18",
      "deployStatus":"installing",
      "healthStatus":"undefined",
      "latestRestart":null,
      "nodes":[
        {
          "id":4,
          "kclusterID":2,
          "kroles":[
            "master"
          ],
          "Etcd":true,
          "controlIP":"10.0.2.54"
        },
        {
          "id":5,
          "kclusterID":2,
          "kroles":[
            "master"
          ],
          "Etcd":true,
          "controlIP":"10.0.2.55"
        },
        {
          "id":6,
          "kclusterID":2,
          "kroles":[
            "worker"
          ],
          "Etcd":true,
          "controlIP":"10.0.2.56"
        }
      ],
      "apps":[
        {
          "ID":2,
          "kclusterID":2,
          "label":"ES2",
          "appName":"elasticsearch",
          "appNamespace":"default",
          "gitUrl":"https://github.com/helm/charts",
          "gitRepoPath":"stable",
          "gitBranch":"master",
          "helmValuesFile":"bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo="
        }
      ],
      "latestAnsibleJob":{
        "ID":49,
        "Label":"deploy",
        "target":"kubernetes.cluster",
        "targetID":104,
        "cwDir":"ops/ansible-systems",
        "wsDir":"ops/ansible-systems/inventories/gopalcluster",
        "playbook":"app-deploy.yml",
        "vars":"",
        "customArgs":[
          "--flush-cache",
          "-b",
          "-e",
          "action=\"deploy\"",
          "-e",
          "apps=/home/ops/ansible-systems/inventories/gopalcluster/apps.yml"
        ],
        "inventory":"\n[all:vars]\nansible_ssh_user = pcc\nansible_ssh_private_key_file = /root/.ssh/id_rsa_ansible\nansible_ssh_common_args='-o StrictHostKeyChecking=no'\nkube_pods_subnet = 10.2.64.0/18\nkube_version = v1.12.7\nkube_network_plugin = kube-router\nreset_restart_network = false\ncluster_name = gopalcluster\nkube_service_addresses = 10.2.0.0/18\n\n[all] \nsjc01-pd1-lf06 ansible_host=172.17.2.59 ip=10.0.2.59 \nnode-sv13 ansible_host=172.17.2.113 ip=10.0.2.113 \nnode-sv12 ansible_host=172.17.2.112 ip=10.0.2.112 \n\n[kube-master]   \nsjc01-pd1-lf06       \n\n[kube-node]     \nnode-sv13   \nnode-sv12   \n\n[etcd]  \nsjc01-pd1-lf06   \nnode-sv13   \nnode-sv12  \n\n[k8s-cluster:children]\nkube-node\nkube-master\n",
        "logPath":"jobs/kubernetes/cluster/104/2019-06-18_14.53.48.749707_UTC-app-deploy-deploy/ansible.log",
        "startTime":"2019-06-18T14:53:48.750293Z",
        "progressPercentage":0,
        "endTime":"2019-06-18T14:53:54.322242Z",
        "result":2,
        "aborted":false
      }
    }
  ]
}
```


### Get specific cluster

Returns specific cluster information

#### Curl example
```
curl -k -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes/1'
```

#### Request URL

**GET**

http://127.0.0.1:8080/kubernetes/1

#### Response

Ansible Parameter

Here latest ansible job executed on cluster is on latestAnsibleJob parameter.

See Ansible section on this guide to check how to sync with ansible job logs at runtime via websocket.

```JSONasPython
{
  "path": "",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
	"ID": 2,
	"name": "cluster.test2",
	"networkID": 2,
	"rolePolicy": "auto",
	"k8sVersion": "v1.12.7",
	"cniPlugin": "kube-router",
	"servicesCIDR": "10.2.0.0/18",
	"podsCIDR": "10.2.64.0/18",
	"deployStatus": "installing",
	"healthStatus": "undefined",
	"latestRestart": null,
	"nodes": [
  	{
    	"id": 4,
    	"kclusterID": 2,
    	"kroles": [
      	"master"
    	],
    	"Etcd": true,
    	"controlIP": "10.0.2.54"
  	},
  	{
    	"id": 5,
    	"kclusterID": 2,
    	"kroles": [
      	"master"
    	],
    	"Etcd": true,
    	"controlIP": "10.0.2.55"
  	},
  	{
    	"id": 6,
    	"kclusterID": 2,
    	"kroles": [
      	"worker"
    	],
    	"Etcd": true,
    	"controlIP": "10.0.2.56"
  	}
	],
	"apps": [
  	{
    	"ID": 2,
    	"kclusterID": 2,
    	"label": "ES2",
    	"appName": "elasticsearch",
    	"appNamespace": "default",
    	"gitUrl": "https://github.com/helm/charts",
    	"gitRepoPath": "stable",
    	"gitBranch": "master",
    	"helmValuesFile": "bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo="
  	}
	],
"latestAnsibleJob":{
        "ID":49,
        "Label":"deploy",
        "target":"kubernetes.cluster",
        "targetID":104,
        "cwDir":"ops/ansible-systems",
        "wsDir":"ops/ansible-systems/inventories/gopalcluster",
        "playbook":"app-deploy.yml",
        "vars":"",
        "customArgs":[
          "--flush-cache",
          "-b",
          "-e",
          "action=\"deploy\"",
          "-e",
          "apps=/home/ops/ansible-systems/inventories/gopalcluster/apps.yml"
        ],
        "inventory":"\n[all:vars]\nansible_ssh_user = pcc\nansible_ssh_private_key_file = /root/.ssh/id_rsa_ansible\nansible_ssh_common_args='-o StrictHostKeyChecking=no'\nkube_pods_subnet = 10.2.64.0/18\nkube_version = v1.12.7\nkube_network_plugin = kube-router\nreset_restart_network = false\ncluster_name = gopalcluster\nkube_service_addresses = 10.2.0.0/18\n\n[all] \nsjc01-pd1-lf06 ansible_host=172.17.2.59 ip=10.0.2.59 \nnode-sv13 ansible_host=172.17.2.113 ip=10.0.2.113 \nnode-sv12 ansible_host=172.17.2.112 ip=10.0.2.112 \n\n[kube-master]   \nsjc01-pd1-lf06       \n\n[kube-node]     \nnode-sv13   \nnode-sv12   \n\n[etcd]  \nsjc01-pd1-lf06   \nnode-sv13   \nnode-sv12  \n\n[k8s-cluster:children]\nkube-node\nkube-master\n",
        "logPath":"jobs/kubernetes/cluster/104/2019-06-18_14.53.48.749707_UTC-app-deploy-deploy/ansible.log",
        "startTime":"2019-06-18T14:53:48.750293Z",
        "progressPercentage":0,
        "endTime":"2019-06-18T14:53:54.322242Z",
        "result":2,
        "aborted":false
      }
  }
}
```

### Update specific cluster

Add a new kubernetes cluster

#### Curl example
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes' -d '{"rolePolicy":"auto","toRemove":[1,2],"toAdd":[{"id":4,"roles":["master"],"etcd":true},{"id":5,"roles":["master"]}]}'
```

#### Request URL

**PUT**
http://127.0.0.1:8080/kubernetes/1


#### Request Body

With **auto**policy:
```
{
  "rolePolicy":"auto",
  "toRemove":[
    1,
    2
  ],
  "toAdd":[
    {
      "id":4
    },
    {
      "id":5
    }
  ]
}
```

With **custom** policy:
```JSONasPython
{
  "rolePolicy":"custom",
  "toRemove":[
    1,
    2
  ],
  "toAdd":[
    {
      "id":3,
      "roles":[
        "master"
      ],
      "etcd":false
    },
    {
      "id":4,
      "roles":[
        "worker"
      ],
      "etcd":true
    },
    {
      "id":10,
      "roles":[
        "worker"
      ],
      "etcd":true
    }
  ]
}
```

#### Response
```JSONasPython
{
  "path": "",
  "status": 200,
  "message": "Cluster with id [12] is going to be updated",
  "error": ""
}
```

### Delete specific cluster

Returns specific cluster information

#### Curl example
```
curl -k  -X DELETE -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes/1'
```

#### Request URL

**DELETE**

http://127.0.0.1:8080/kubernetes/1

#### Request Body
```JSONasPython
{
"forceRemove": true
}
```

#### Response
```JSONasPython
{
  "path": "",
  "status": 200,
  "message": "Cluster with id [12] is going to be removed",
  "error": ""
}
```

### Deploy Kubernetes Application


Deploy applications on existing kubernetes application

**NOTE**:
File related to base64 on the example is:
```
master:
  persistence:
	enabled: false
data:
  persistence:
	enabled: false
```

**GUI example**

Name: ES

App Name: **elasticsearch**

App Namespace: default
gitUrl: [https://github.com/helm/charts](https://github.com/helm/charts","gitRepoPath":"stable","gitBranch":"master","helmValuesFile":"bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo=)

gitRepoPath: stable
gitBranch: master
helm values:
```
master:
  persistence:
	enabled: false
data:
  persistence:
	enabled: false
```

#### Curl example
##### Elastic Search
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MTM4NTg4NywiaWF0IjoxNTYwNzgxMDg3fQ.GtevBCMbBXQzlrhY7j1zzWBK_2Lg_8jTX0KI1FJRPvjVEYyHNYrR2C-9-IEwey-jXJ3CkiS5QCAIx6q0kiicpg" 'https://127.0.0.1:9999/pccserver/kubernetes/112/app/' -d '[{"label":"ES","appName":"elasticsearch","appNamespace":"default","gitUrl":"https://github.com/helm/charts","gitRepoPath":"stable","gitBranch":"master","helmValuesFile":"bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo="}]'
```
##### Nginx
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MTM4NTg4NywiaWF0IjoxNTYwNzgxMDg3fQ.GtevBCMbBXQzlrhY7j1zzWBK_2Lg_8jTX0KI1FJRPvjVEYyHNYrR2C-9-IEwey-jXJ3CkiS5QCAIx6q0kiicpg" 'https://127.0.0.1:9999/pccserver/kubernetes/112/app/' -d '[{"label":"NG","appName":"nginxapp","appNamespace":"nginxapp","gitUrl":"https://platinasystems:e2939d936e189f689b4f62ffd30a026109e362c4@github.com/platinasystems/ops","gitRepoPath":"k8s/apps/helm-charts","gitBranch":"master","helmValuesFile":""}]'
```

##### Wordpress
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MTM4NTg4NywiaWF0IjoxNTYwNzgxMDg3fQ.GtevBCMbBXQzlrhY7j1zzWBK_2Lg_8jTX0KI1FJRPvjVEYyHNYrR2C-9-IEwey-jXJ3CkiS5QCAIx6q0kiicpg" 'https://127.0.0.1:9999/pccserver/kubernetes/112/app/' -d '[{"label":"WP","appName":"wordpress-mysql","appNamespace":"wordpress-mysql","gitUrl":"https://platinasystems:e2939d936e189f689b4f62ffd30a026109e362c4@github.com/platinasystems/ops","gitRepoPath":"k8s/apps/helm-charts","gitBranch":"master","helmValuesFile":""}]'
```

#### Request URL

http://127.0.0.1:8080/kubernetes/:id/apps


#### Request Body
```
[
  {
    "label":"ES",
    "appName":"elasticsearch",
    "appNamespace":"default",
    "gitUrl":"https://github.com/helm/charts",
    "gitRepoPath":"stable",
    "gitBranch":"master",
    "helmValuesFile":"bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo="
  },
  {
    "label":"ES2",
    "appName":"elasticsearch",
    "appNamespace":"default",
    "gitUrl":"https://github.com/helm/charts",
    "gitRepoPath":"stable",
    "gitBranch":"master",
    "helmValuesFile":"bWFzdGVyOgogIHBlcnNpc3RlbmNlOgogICAgZW5hYmxlZDogZmFsc2UKZGF0YToKICBwZXJzaXN0ZW5jZToKICAgIGVuYWJsZWQ6IGZhbHNlCgo="
  }
]
```

#### Response
```
{
  "path": "",
  "status": 200,
  "message": "Applications are going to be installed on cluster with id [1]",
  "error": ""
}
```

### Undeploy Kubernetes Application


Undeploy an application from existing kubernetes application

#### Curl example
```
curl -k  -X DELETE -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2MDU5NTE4OCwiaWF0IjoxNTU5OTkwMzg4fQ.JxN1dkjmmiH1P5_CA6bRVkfbL2kcdmwQ0qGdF4YJv9dzxLsG3fSdsW-R-MW00EISQSYTF3CsVE5WuZN8lOBD7g" 'https://127.0.0.1:9999/pccserver/kubernetes/103/app/' -d '{"appIds": [1,2]}'
```

#### Request URL

http://127.0.0.1:8080/kubernetes/:id/apps

#### Response
```
{
  "path": "",
  "status": 200,
  "message": "Applications with IDs [[1]] are going to be undeployed from cluster with id [1]",
  "error": ""
}
```

### Upgrade/Downgrade Kubernetes Cluster


Upgrade or downgrade kubernetes cluster to a specific version

#### Curl example
```
curl -k  -X POST -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTU2Mjc1MzU0MSwiaWF0IjoxNTYyMTQ4NzQxfQ.gPpFfagk7VMvdaS3CNdlwk4GJI9SjYSx6S9JSAmF03H0m3SWo1iafLNItc6FnI0laU7elVAfT2oOYWtibF-1-g" 'https://127.0.0.1:9999/pccserver/kubernetes/4/upgrade' -d '{"k8sVersion": "v1.14.3"}'
```

#### Request Body
```
{
  "k8sVersion":"v1.13.5",
  "cniPlugin":"kube-router",
}
```

#### Request URL

**POST**

http://127.0.0.1:8080/kubernetes/1/upgrade


#### Response
```
{
  "path": "",
  "status": 200,
  "message": "Cluster with ID [1] is going to be upgraded to version [v1.13.5]",
  "error": ""
}
```

## Ansible

The following operations related to specific ansible jobs are stored on database in order to be retrieved within the related target via pccserver:

Target
GET Requests with job details included
Parameter
kubernetes.cluster
kubernetes/:id
kubernetes
latestAnsibleJob

<table>
  <tr>
    <td>Operation</td>
    <td>Endpoint</td>
    <td>Method</td>
    <td>Note</td>
  </tr>
  <tr>
    <td>Get ansible job</td>
    <td>ansible/:id</td>
    <td>GET</td>
    <td></td>
  </tr>
  <tr>
    <td>Get ansible job logs</td>
    <td>ansible/:id/logs</td>
    <td>Websocket</td>
    <td></td>
  </tr>
  <tr>
    <td>Get ansible target history</td>
    <td>ansible/history?target=kubernetes.cluster&target_id=1</td>
    <td>GET</td>
    <td>The request support pagination</td>
  </tr>
</table>


### Get job

Returns specific job details

#### Response
```JSONasPython
{
  "path": "/ansible/69",
  "status": 200,
  "message": "",
  "error": "",
  "Data": {
    "ID": 69,
    "Label": "undeploy",
    "target": "kubernetes.cluster",
    "targetID": 113,
    "cwDir": "ops/ansible-systems",
    "wsDir": "ops/ansible-systems/inventories/ctl-app-demo",
    "playbook": "app-deploy.yml",
    "vars": "",
    "customArgs": [
      "--flush-cache",
      "-b",
      "-e",
      "action=\"undeploy\"",
      "-e",
      "apps=/home/ops/ansible-systems/inventories/ctl-app-demo/apps.yml"
    ],
    "inventory": "\n[all:vars]\nansible_ssh_user = pcc\nansible_ssh_private_key_file = /root/.ssh/id_rsa_ansible\nansible_ssh_common_args='-o StrictHostKeyChecking=no'\nkube_pods_subnet = 10.2.64.0/18\nkube_version = v1.12.7\nkube_network_plugin = kube-router\nreset_restart_network = false\ncluster_name = ctl-app-demo\nkube_service_addresses = 10.2.0.0/18\n\n[all] \nsjc01-pd1-lf06 ansible_host=172.17.2.59 ip=10.0.2.59 \nnode-sv12 ansible_host=172.17.2.112 ip=10.0.2.112 \nnode-sv13 ansible_host=172.17.2.113 ip=10.0.2.113 \n\n[kube-master]   \nsjc01-pd1-lf06       \n\n[kube-node]     \nnode-sv12   \nnode-sv13   \n\n[etcd]  \nsjc01-pd1-lf06   \nnode-sv12   \nnode-sv13  \n\n[k8s-cluster:children]\nkube-node\nkube-master\n",
    "logPath": "jobs/kubernetes/cluster/113/2019-06-18_20.47.21.801363_UTC-app-deploy-undeploy/ansible.log",
    "startTime": "2019-06-18T20:47:21.802654Z",
    "progressPercentage": 0,
    "endTime": "2019-06-18T20:47:29.089431Z",
    "result": 0,
    "aborted": false
  }
}
```

### Get job logs

Websocket endpoint to get logs generated at runtime for given ansible job

Client will receive a message for each line that is written on the related log file.

### Get target job history

Returns all jobs related to a specific target identified by:

**target**: the job target ( e.g. kubernetes.cluster )

**targetId**: the target identifier ( e.g. the kubernetes cluster identifier )

**Example**

```
GET https://172.17.2.47:9999/pccserver/ansible/history?target=kubernetes.cluster&target_id=112&search=playbook:cluster.yml
```

#### Response
```JSONasPython
{
  "path": "/ansible/history?target=kubernetes.cluster&target_id=112",
  "status": 200,
  "message": "",
  "error": "",
  "Data": [
    {
      "ID": 65,
      "Label": "deploy",
      "target": "kubernetes.cluster",
      "targetID": 112,
      "cwDir": "ops/ansible-systems",
      "wsDir": "ops/ansible-systems/inventories/gregcluster",
      "playbook": "app-deploy.yml",
      "vars": "",
      "customArgs": [
        "--flush-cache",
        "-b",
        "-e",
        "action=\"deploy\"",
        "-e",
        "apps=/home/ops/ansible-systems/inventories/gregcluster/apps.yml"
      ],
      "inventory": "\n[all:vars]\nansible_ssh_user = pcc\nansible_ssh_private_key_file = /root/.ssh/id_rsa_ansible\nansible_ssh_common_args='-o StrictHostKeyChecking=no'\nkube_pods_subnet = 10.1.64.0/18\nkube_version = v1.12.7\nkube_network_plugin = kube-router\nreset_restart_network = false\ncluster_name = gregcluster\nkube_service_addresses = 10.1.0.0/18\n\n[all] \ni36-sjc01-pd1-lf01 ansible_host=172.17.2.36 ip=10.0.1.36 \nsjc01-pd1-sv02 ansible_host=172.17.2.252 ip=10.0.1.252 \nsjc01-pd1-sv01 ansible_host=172.17.2.251 ip=10.0.1.251 \n\n[kube-master]   \ni36-sjc01-pd1-lf01       \n\n[kube-node]     \nsjc01-pd1-sv02   \nsjc01-pd1-sv01   \n\n[etcd]  \ni36-sjc01-pd1-lf01   \nsjc01-pd1-sv02   \nsjc01-pd1-sv01  \n\n[k8s-cluster:children]\nkube-node\nkube-master\n",
      "logPath": "jobs/kubernetes/cluster/112/2019-06-18_20.37.42.316704_UTC-app-deploy-deploy/ansible.log",
      "startTime": "2019-06-18T20:37:42.317229Z",
      "progressPercentage": 0,
      "endTime": "2019-06-18T20:39:01.138144Z",
      "result": 0,
      "aborted": false
    },
    {
      "ID": 64,
      "Label": "undeploy",
      "target": "kubernetes.cluster",
      "targetID": 112,
      "cwDir": "ops/ansible-systems",
      "wsDir": "ops/ansible-systems/inventories/gregcluster",
      "playbook": "app-deploy.yml",
      "vars": "",
      "customArgs": [
        "--flush-cache",
        "-b",
        "-e",
        "action=\"undeploy\"",
        "-e",
        "apps=/home/ops/ansible-systems/inventories/gregcluster/apps.yml"
      ],
      "inventory": "\n[all:vars]\nansible_ssh_user = pcc\nansible_ssh_private_key_file = /root/.ssh/id_rsa_ansible\nansible_ssh_common_args='-o StrictHostKeyChecking=no'\nkube_pods_subnet = 10.1.64.0/18\nkube_version = v1.12.7\nkube_network_plugin = kube-router\nreset_restart_network = false\ncluster_name = gregcluster\nkube_service_addresses = 10.1.0.0/18\n\n[all] \ni36-sjc01-pd1-lf01 ansible_host=172.17.2.36 ip=10.0.1.36 \nsjc01-pd1-sv02 ansible_host=172.17.2.252 ip=10.0.1.252 \nsjc01-pd1-sv01 ansible_host=172.17.2.251 ip=10.0.1.251 \n\n[kube-master]   \ni36-sjc01-pd1-lf01       \n\n[kube-node]     \nsjc01-pd1-sv02   \nsjc01-pd1-sv01   \n\n[etcd]  \ni36-sjc01-pd1-lf01   \nsjc01-pd1-sv02   \nsjc01-pd1-sv01  \n\n[k8s-cluster:children]\nkube-node\nkube-master\n",
      "logPath": "jobs/kubernetes/cluster/112/2019-06-18_20.34.12.564185_UTC-app-deploy-undeploy/ansible.log",
      "startTime": "2019-06-18T20:34:12.564656Z",
      "progressPercentage": 0,
      "endTime": "2019-06-18T20:34:23.103012Z",
      "result": 0,
      "aborted": false
    },
    {
      "ID": 63,
      "Label": "deploy",
      "target": "kubernetes.cluster",
      "targetID": 112,
      "cwDir": "ops/ansible-systems",
      "wsDir": "ops/ansible-systems/inventories/gregcluster",
      "playbook": "app-deploy.yml",
      "vars": "",
      "customArgs": [
        "--flush-cache",
        "-b",
        "-e",
        "action=\"deploy\"",
        "-e",
        "apps=/home/ops/ansible-systems/inventories/gregcluster/apps.yml"
      ],
      "inventory": "\n[all:vars]\nansible_ssh_user = pcc\nansible_ssh_private_key_file = /root/.ssh/id_rsa_ansible\nansible_ssh_common_args='-o StrictHostKeyChecking=no'\nkube_pods_subnet = 10.1.64.0/18\nkube_version = v1.12.7\nkube_network_plugin = kube-router\nreset_restart_network = false\ncluster_name = gregcluster\nkube_service_addresses = 10.1.0.0/18\n\n[all] \ni36-sjc01-pd1-lf01 ansible_host=172.17.2.36 ip=10.0.1.36 \nsjc01-pd1-sv02 ansible_host=172.17.2.252 ip=10.0.1.252 \nsjc01-pd1-sv01 ansible_host=172.17.2.251 ip=10.0.1.251 \n\n[kube-master]   \ni36-sjc01-pd1-lf01       \n\n[kube-node]     \nsjc01-pd1-sv02   \nsjc01-pd1-sv01   \n\n[etcd]  \ni36-sjc01-pd1-lf01   \nsjc01-pd1-sv02   \nsjc01-pd1-sv01  \n\n[k8s-cluster:children]\nkube-node\nkube-master\n",
      "logPath": "jobs/kubernetes/cluster/112/2019-06-18_20.23.40.644900_UTC-app-deploy-deploy/ansible.log",
      "startTime": "2019-06-18T20:23:40.645461Z",
      "progressPercentage": 0,
      "endTime": "2019-06-18T20:24:01.653774Z",
      "result": 0,
      "aborted": false
    }
  ]
}
```
