<h1>ActiveConnections</h1>

Listar todos os IP conectados ao seu computador
```ps1
netstat -an | Select-String "ESTABLISHED" | ForEach-Object {
    $line = $_ -split "\s+"
    $localAddress = $line[1]
    $foreignAddress = $line[2]
    Write-Host "Conexão estabelecida de $localAddress para $foreignAddress"
}
```
<br>

<strong> netstat </strong>

<p> Exibe conexões TCP ativas, portas nas quais o computador está em escuta, estatísticas de Ethernet, tabela de roteamento de IP, estatísticas de IPv4 (para os protocolos IP, ICMP, TCP e UDP) e estatísticas de IPv6 (para os protocolos IPv6, ICMPv6, TCP sobre IPv6 e UDP sobre IPv6). Usado sem parâmetros, esse comando exibe conexões TCP ativas. </p>

- Documentação: https://learn.microsoft.com/pt-br/windows-server/administration/windows-commands/netstat

<strong> Sintaxe </strong>

```ps1
netstat [-a] [-b] [-e] [-n] [-o] [-p <Protocol>] [-r] [-s] [<interval>]
```
<strong> Exibir todas as conexões de rede ativas: </strong>

```ps1
netstat
```
<strong> Listar conexões TCP e UDP: </strong> 

```ps1
netstat -a
```


<strong>Exibir as estatísticas de Ethernet e as estatísticas de todos os protocolos: </strong> 

```ps1
netstat -e -s
```
![image](https://github.com/oanderoficial/ActiveConnections/assets/32654298/f892657c-1ccf-413c-87d0-b7decf2aa387)

<strong> Exibir as estatísticas apenas para os protocolos TCP e UDP: </strong>

```ps1
netstat -s -p tcp
```

```ps1
netstat -s -p udp
```

 <strong> Exibir conexões TCP ativas e as IDs de processo a cada 5 segundos: </strong>

 ```ps1
netstat -o 5
```

<strong> Exibir conexões TCP ativas e as IDs de processo usando o formulário numérico: </strong>

```ps1
netstat -n -o
```

<strong> Exibir apenas as conexões de escuta (portas abertas):  </strong>

```ps1
netstat -aon | findstr "LISTENING"
```
<strong> Verificar conexões para um endereço IP ou nome de host específico: </strong> 

```ps1
netstat -aon | findstr "192.168.1.100"
```
<strong>Exibir estatísticas de roteamento: </strong>

```ps1
netstat -r
```

<strong> Mostrar estatísticas de interface de rede: </strong>
    
```ps1 
netstat -s
```
<strong>  cmdlet Test-NetConnection  </strong>

<p>O Test-NetConnection oferece uma variedade de opções que permitem personalizar os testes. As opções mais comuns incluem: </p>

- -ComputerName:  Especifica o nome do computador ou endereço IP do destino.
- -Port: Especifica a porta TCP a ser testada.
- -Count: Especifica o número de pacotes a serem enviados.
- -Size: Especifica o tamanho dos pacotes em bytes.
- -Timeout: Especifica o tempo limite para os testes em segundos.
- -InformationLevel: Especifica o nível de informação a ser exibido nos resultados. Os níveis válidos são Basic, Detailed e Verbose.

<strong> Test-NetConnection Documentação: </storng> 
<br>
-->  https://learn.microsoft.com/en-us/powershell/module/nettcpip/test-netconnection?view=windowsserver2022-ps

<h2> Exemplos: </h2>

<strong> Testar a conectividade com um site: </strong>

```ps1
Test-NetConnection -ComputerName www.oander.site
```
![image](https://github.com/oanderoficial/ActiveConnections/assets/32654298/aa29991f-1658-4713-a3b4-e9bde0456a5b)

<strong> Testar a conectividade com um servidor em uma porta específica: </strong>

```ps1
Test-NetConnection -ComputerName server1 -Port 80
```
![image](https://github.com/oanderoficial/ActiveConnections/assets/32654298/7ff1187b-d734-4f9d-bb5e-4382d5148bbc)


<strong> Traçar a rota para um destino: </strong>

```ps1
Test-NetConnection -ComputerName server2 -Trace
```

<strong>  Testando com parâmetros personalizados: </strong> 

```ps1
Test-NetConnection -ComputerName www.oander.site -Count 10 -Size 2048 -Timeout 5 -InformationLevel Detailed
```
<br>
<br>

<strong> cmdlet Get-NetIPAddress. </strong>

<p> O cmdlet Get-NetIPAddress obtém a configuração do endereço IP, como endereços IPv4, endereços IPv6 e as interfaces IP às quais os endereços estão associados. Sem parâmetros, este cmdlet obtém toda a configuração do endereço IP do computador.</p>

<h2> Exemplos: </h2> 

<strong> Obter informações sobre todos os adaptadores de rede: </strong>

```ps1
Get-NetIPAddress
```
<strong> Obter informações sobre um adaptador de rede específico: </strong> 

```ps1
Get-NetIPAddress -InterfaceAlias Ethernet
```
<strong> Obtenha informações de endereços IP's formatando a saída: </strong>

```ps1
Get-NetIPAddress | Format-Table
```
<strong> Obter informações de endereço IP pelo índice da interface (ifIndex): </strong>

```ps1
Get-NetIPAddress -InterfaceIndex 17
````

<strong> Filtrar resultados por família de endereço (IPv4 ou IPv6):  </strong>

```ps1
Get-NetIPAddress -AddressFamily IPv4
```

- Documentação do Get-NetIPAddress:
  https://abrir.link/DAesG
- Exemplos de Get-NetIPAddress:
  https://abrir.link/DAesG
