# devop_configuration


#THIS SHOULD BE THE CONFIGURATIO  OF THE VIRTUAL NETWORK ADAPTER IN THE  VMWARE:
<img width="680" height="656" alt="image" src="https://github.com/user-attachments/assets/ce582cbd-010d-4aff-83cc-0ecec40f3336" />


#this must be the network adpater configurion after you add the network adapters:
<img width="978" height="439" alt="image" src="https://github.com/user-attachments/assets/94d09732-f6ce-4596-88bb-c77ba2bac36e" />

#NEXT PASTE THIS IN THE CSR100V
config t
int gi 2
no shut
ip add 192.168.102.11 255.255.255.0
line vty 0 14
exec-timeout 0 0
transport input all
iox
interface GigabitEthernet1
ip address dhcp
ip nat outside
no shut
exit
!
interface VirtualPortGroup0
ip address 192.168.35.1 255.255.255.0
ip nat inside
exit
!
ip nat inside source list GS_NAT_ACL interface GigabitEthernet1 overload
ip access-list standard GS_NAT_ACL
permit 192.168.0.0 0.0.255.255
!
app-hosting appid guestshell
 app-vnic gateway1 virtualportgroup 0 guest-interface 0
    guest-ipaddress 192.168.35.3 netmask 255.255.255.0	
	app-default-gateway 192.168.35.1  guest-interface 0 
	name-server0 1.1.1.1
 app-resource profile custom 
   cpu 1500 
   memory 512
end

#SH IP INT BRI PARA MAKAPASOK SA SECURE CRT USING TELNET

#GAWA NG CLONSE SESSION TATLONG BESES AT ITYPE TONG MGA COMMAND EACH SA SESSION NA YUN
UNANGTELNET enables DOCKERIzation:  guestshell enable (1st session yung  cisco)
2NDtELNET run python docker via reddhat using on cisco:    guestshell run python3 (python)
THIRDTELNET:  guestshell run bash (linux)
this is the product:
<img width="817" height="425" alt="image" src="https://github.com/user-attachments/assets/1fd0f0b1-aeef-4227-b4c2-7d93d9791ec3" />


#next step add ito sa linux
dahil hindi niya nagagawa yung yum install.
<img width="809" height="425" alt="image" src="https://github.com/user-attachments/assets/c816e286-66c2-4edc-999b-35f860eea6c7" />

sudo su
cd /etc/yum.repos.d/
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
yum update -y


#PYTHON script for sh ip int bri
import cli

k = [
    "show ip int brief"
]

for k in mycmd1:
    cli.executep(k)


#NOW CREATING A LOOPBACK VIA PYTHON GOING THRU THE CISCO
import cli

cmd1 = '''hostname NETDEVOPS
int loop 4
ip add 4.4.4.4 255.255.255.255
int loop 5
ip add 5.5.5.5 255.255.255.255
int loop 6
ip add 6.6.6.6 255.255.255.255
end
'''
cli.configurep(cmd1)


##EX2

import cli

cmd1 = '''ip dhcp pool pythonpool
network 4.4.4.0 255.255.255.0
default-router 4.4.4.4
end
'''
cli.configurep(cmd1)

####NEXT IS TO ACTIVATE POSTMAN ACCOUNT IN CISCO
<img width="774" height="422" alt="image" src="https://github.com/user-attachments/assets/bf5f8377-4b6f-4dd4-930c-5b0893d7c7e9" />

config t
!username admin privilege 15 secret pass
ip http secure-server
ip http authentication local
restconf
end


###1ST IMPORT CISCO OIS-XE
<img width="694" height="367" alt="image" src="https://github.com/user-attachments/assets/36ed57cf-1cf8-4c26-a510-a6591157e339" />

####TAS PALITAN IP
<img width="781" height="124" alt="image" src="https://github.com/user-attachments/assets/b0598707-18b5-43fa-b76b-bd17e2bcbeff" />



