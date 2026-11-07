# Onboarding de colaborador — checklist

**Responsável:** Suporte N1 · **Prazo:** pronto até 1 dia antes da data de início

## Informações necessárias (vindas do RH/gestor)
- [ ] Nome completo, cargo, departamento, data de início
- [ ] Gestor responsável
- [ ] Sistemas e pastas que precisa acessar (aprovados pelo gestor)
- [ ] Equipamento: notebook ou desktop, periféricos, celular

## Contas e acessos
- [ ] Criar usuário no Active Directory na OU do departamento (padrão `nome.sobrenome`) — script: [`Criar-UsuariosAD.ps1`](https://github.com/CassioX/scripts-suporte/blob/main/windows/Criar-UsuariosAD.ps1)
- [ ] Senha temporária com **troca obrigatória no primeiro logon**
- [ ] Adicionar aos grupos do departamento (pastas, impressoras, VPN)
- [ ] Criar caixa de e-mail e atribuir licença (ex.: Microsoft 365)
- [ ] Incluir em listas de distribuição e Teams do setor
- [ ] Acessos a sistemas específicos (ERP, CRM) — chamado para o responsável de cada sistema
- [ ] Configurar MFA (autenticação em dois fatores)

## Equipamento
- [ ] Máquina preparada conforme [padrão](preparacao-maquina.md)
- [ ] Registrar patrimônio / número de série no inventário vinculado ao colaborador
- [ ] Termo de responsabilidade do equipamento assinado
- [ ] Testar login com o usuário criado, mapeamento de pastas e impressora

## Primeiro dia
- [ ] Entregar equipamento e credenciais (pessoalmente ou por canal seguro — **nunca senha por e-mail ao gestor em texto aberto**)
- [ ] Ajudar na troca de senha e configuração do MFA
- [ ] Apresentar como abrir chamados no suporte
- [ ] Passar orientações de segurança: phishing, bloqueio de tela (`Win + L`), senhas

## Encerramento
- [ ] Atualizar o chamado com tudo que foi feito e encerrar
