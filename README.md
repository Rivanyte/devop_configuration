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
<img width="809" height="425" alt="image" src="https://github.com/user-attachments/assets/c816e286-66c2-4edc-999b-35f860eea6c7" />

sudo su
cd /etc/yum.repos.d/
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
yum update -y




