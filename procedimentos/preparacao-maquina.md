# Preparação de estação de trabalho (padrão)

**Nível:** N1 · **Tempo médio:** 1h30–3h

## Antes de formatar (máquina em uso)
- [ ] Backup dos dados do usuário: Desktop, Documentos, Downloads, favoritos do navegador, assinaturas do Outlook
- [ ] Anotar programas específicos instalados e impressoras
- [ ] Confirmar com o usuário que nada ficou de fora

## Instalação
- [ ] BIOS/UEFI atualizada, boot seguro habilitado, modo AHCI
- [ ] Instalar Windows 11 Pro (pendrive criado com a Media Creation Tool ou imagem padrão)
- [ ] Drivers do fabricante (Dell Command Update, Lenovo Vantage, HP Support Assistant)
- [ ] Windows Update até não haver pendências
- [ ] Renomear: padrão `SETOR-PATRIMONIO` (ex.: `FIN-00123`)
- [ ] Ingressar no domínio / Entra ID

## Softwares padrão
Instalação rápida via winget:
```powershell
winget install -e --id Google.Chrome
winget install -e --id 7zip.7zip
winget install -e --id Adobe.Acrobat.Reader.64-bit
winget install -e --id Microsoft.Teams
```
- [ ] Microsoft 365 / Office
- [ ] Antivírus / EDR corporativo
- [ ] Agente de acesso remoto e inventário
- [ ] VPN (se necessário)
- [ ] Softwares específicos do setor

## Segurança
- [ ] BitLocker ativado e chave de recuperação salva no AD/Entra ID
- [ ] Usuário **sem** privilégio de administrador local
- [ ] Bloqueio de tela automático (10 min)

## Finalização
- [ ] Restaurar backup do usuário
- [ ] Mapear unidades de rede e impressoras
- [ ] Testar com o usuário: login, e-mail, sistemas, impressão
- [ ] Atualizar inventário e encerrar o chamado
