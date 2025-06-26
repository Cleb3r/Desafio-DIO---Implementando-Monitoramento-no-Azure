# 🛠️ Monitoramento via Azure CLI: Exemplo de Alerta para Exclusão de VM

Este documento mostra como criar um alerta baseado no log de atividade usando Azure CLI.

## 1. Criar Grupo de Ação com Notificação
```
az monitor action-group create \
  --resource-group MeuGrupoDeRecursos \
  --name acaoAlertaVM \
  --short-name alertaVM \
  --action email alertaEmail SEU_EMAIL@exemplo.com
```
## 2. Criar Regra de Alerta para Exclusão de VM
```
az monitor activity-log alert create \
  --name alertaExclusaoVM \
  --resource-group MeuGrupoDeRecursos \
  --scopes /subscriptions/SUBSCRIPTION_ID \
  --condition "category=Administrative and operationName=Delete Virtual Machine" \
  --action-group alertaVM
```
> Substitua SUBSCRIPTION_ID pelo seu ID de assinatura (use az account show para descobrir)

## 3. Visualizar Alertas Criados
```
az monitor activity-log alert list --output table
```
## 4. Verificar logs de exclusão de VM manualmente (consulta direta)
```
az monitor activity-log list \
  --resource-group MeuGrupoDeRecursos \
  --status "Succeeded" \
  --offset 1d \
  --query "[?operationName.value=='Microsoft.Compute/virtualMachines/delete']"
```
