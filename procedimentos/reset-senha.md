# Reset de senha e desbloqueio de conta

**Nível:** N1 · **Tempo médio:** 5 min

## 1. Validar a identidade (obrigatório)
Engenharia social é uma das formas mais comuns de invasão — **nunca** redefina senha só porque alguém pediu por telefone ou chat.

Confirme pelo menos dois itens:
- Matrícula / CPF parcial cadastrado no RH
- Ligação de volta para o ramal ou celular **cadastrado** (não o informado na hora)
- Confirmação do gestor imediato
- Pedido feito pessoalmente com crachá

## 2. Conta bloqueada x senha esquecida
Verificar no AD (PowerShell):
```powershell
Get-ADUser nome.sobrenome -Properties LockedOut, PasswordExpired, PasswordLastSet, BadLogonCount, LastBadPasswordAttempt
```

| Situação | Ação |
|---|---|
| `LockedOut = True` e o usuário lembra a senha | Apenas desbloquear: `Unlock-ADAccount nome.sobrenome` |
| Esqueceu a senha | Resetar (passo 3) |
| `PasswordExpired = True` | Resetar ou orientar troca |
| Bloqueia de novo em minutos | Senha antiga salva em celular/Outlook/unidade mapeada tentando logar — localizar a origem (evento **4740** no controlador de domínio) |

## 3. Resetar
```powershell
Set-ADAccountPassword nome.sobrenome -Reset -NewPassword (Read-Host -AsSecureString "Senha temporária")
Set-ADUser nome.sobrenome -ChangePasswordAtLogon $true
Unlock-ADAccount nome.sobrenome
```
Ou pela interface: *Usuários e Computadores do Active Directory* → botão direito → Redefinir senha → marcar "O usuário deve alterar a senha no próximo logon".

## 4. Após o reset
- Informar a senha temporária por canal seguro
- Orientar o usuário a atualizar a senha no celular (e-mail, Wi-Fi corporativo)
- Registrar no chamado **como a identidade foi validada** (nunca registrar a senha)
