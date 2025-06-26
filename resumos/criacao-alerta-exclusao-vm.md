# 🚨 Alerta de Exclusão de Máquina Virtual no Azure

Este guia mostra como configurar um alerta para ser notificado sempre que uma máquina virtual for excluída no Azure. Utilizaremos **Azure Monitor**, **Activity Log** e **Action Groups** para disparar notificações por e-mail.

## 1. Acessar o Azure Monitor

- No portal do Azure, busque por **"Monitor"**
- Clique em **"Alertas"** no menu lateral
- Clique em **"Criar" > "Regra de Alerta"**

## 2. Definir o escopo

- Clique em **"Selecionar escopo"**
- Escolha a **assinatura** onde a VM está localizada
- Marque o **grupo de recursos** que deseja monitorar

## 3. Condição do Alerta

- Em “Condição”, clique em **"Adicionar condição"**
- Tipo de sinal: **Log de Atividade**
- Categoria: **Administrative**
- Operação: **Delete Virtual Machine**

## 4. Ações de Resposta (Grupo de Ações)

- Clique em “Adicionar grupo de ações”
- Nome: `notificacao-alerta-vm`
- Tipo de ação: **E-mail/SMS/Push/Voicemail**
- E-mail do responsável: `seu-email@exemplo.com`

> 💡 Você pode adicionar Webhook, Azure Function ou Logic App para automatizar reações.

## 5. Detalhes do Alerta

- Nome: `alerta-exclusao-vm`
- Descrição: Alerta acionado quando uma VM for excluída
- Gravidade: **Alta (Severidade 1 ou 2)**

## 6. Revisar e Criar

- Revise todas as configurações
- Clique em **"Criar Alerta"**
