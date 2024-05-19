# Redes de Computadores

## Planta baixa
![img](/Redes%20de%20Computadores/planta%20baixa%20do%20escritorio.png)

1 Departamentos:

- Vendas
- Ti
- Finanças
- Recursos Humanos
- Sala de reunião

1.2 Equipamentos:

- Notebook Inspiron 15 com Intel® CoreTM i5-1235U (12a geração) 
- placa de vídeo Intel® Iris® Xe Graphics
- 16 GB DDR4 
- 512 GB SSD.

## Classe de rede

Classe de rede C:

 192.168.1.0, sub rede: 255.255.255.0

O rotador é 192.168.1.1, que é o gateway padrão.

2.1 Padrão de rede de cada departamento:

- Vendas: 192.168.1.2 e 192.168.1.12 (DHCP) - 192.168.1.13, estático.
- Ti: 192.168.1.14 - DHCP e 192.168.1.15 - Estático.
- Finanças: 192.168.1.16, estático.
- RH: 192.168.1.17, estático.
- Sala de reunião: 192.168.1.18, estático.

Obs.: O gateway padrão de cada departamento deve ser o IP do roteador.