# 🛠️ Monitoramento via Azure CLI: Exemplo de Alerta para Exclusão de VM

Este documento mostra como criar um alerta baseado no log de atividade usando Azure CLI.

## 1. Criar Grupo de Ação com Notificação

```bash
az monitor action-group create \
  --resource-group MeuGrupoDeRecursos \
  --name acaoAlertaVM \
  --short-name alertaVM \
  --action email alertaEmail SEU_EMAIL@exemplo.com
