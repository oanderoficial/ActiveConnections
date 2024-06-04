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

<strong>  cmdlet Test-NetConnection  </strong>

<p>O Test-NetConnection oferece uma variedade de opções que permitem personalizar os testes. As opções mais comuns incluem: </p>

- -ComputerName:  Especifica o nome do computador ou endereço IP do destino.
- -Port: Especifica a porta TCP a ser testada.
- -Count: Especifica o número de pacotes a serem enviados.
- -Size: Especifica o tamanho dos pacotes em bytes.
- -Timeout: Especifica o tempo limite para os testes em segundos.
- -InformationLevel: Especifica o nível de informação a ser exibido nos resultados. Os níveis válidos são Basic, Detailed e Verbose.

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

<strong> cmdlet Get-NetIPAddress </strong>

<p> Exibe as configurações de IP de um adaptador de rede específico. </p>

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
