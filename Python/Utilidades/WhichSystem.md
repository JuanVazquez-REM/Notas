Esta utilidad tiene como objetivo el *descubrimiento del sistema operativo* de una maquina mediante el TTL de una traza ICMP con *python3*.

Existen muchas herramientas como *nmap* que pueden hacer esto y mas, pero por lo general son muy ruidosas y pueden llamar la atención.

``` python
#!/usr/bin/python3

#re - Para el manejo de expresiones regulares
#sys - Para el manejo de parametros y comando a nivel de sistema
#subprocess - Para lanzar subprocesos

import re, sys, subprocess

if len(sys.argv) != 2:
        print("\n[!] Uso: python3 " + sys.argv[0] + "<ip-address>")
        sys.exit(1)


def get_ttl(ip_address):

	        proc = subprocess.Popen(["/usr/bin/ping -c 1 %s 2>/dev/null" % ip_address, ""], stdout=subprocess.PIPE, shell=True)
        (out,err) = proc.communicate()

        out = out.split()
        out = out[12].decode('utf-8')

        ttl_value = re.findall(r"\d{1,3}", out)[0]
        return ttl_value


def get_os(ttl):
        ttl = int(ttl)

        if(ttl >= 0 and ttl <=64):
                return "Linux"
        elif(ttl >= 65 and ttl <= 128):
                return "Windows"
        else:
                return "Not fount"

if __name__ == '__main__':
        try:
                ip_address = sys.argv[1]
                ttl = get_ttl(ip_address)
                os_name = get_os(ttl)
                print("%s (ttl -> %s): %s" % (ip_address,ttl,os_name))
        except:
                print("\n[!] Uso: python3 " + sys.argv[0] + "<ip-address> ")
                sys.exit(1)
```

