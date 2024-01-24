<h1>ActiveConnection</h1>

Listar todos os IP conectados ao seu computador
```
netstat -an | Select-String "ESTABLISHED" | ForEach-Object {
    $line = $_ -split "\s+"
    $localAddress = $line[1]
    $foreignAddress = $line[2]
    Write-Host "Conexão estabelecida de $localAddress para $foreignAddress"
}
