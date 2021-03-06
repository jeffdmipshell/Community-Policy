# Deploy Diagnostic Settings for Azure Storage blobs to Log Analytics workspace

Deploys the diagnostic settings for Azure Storage blobs to stream to a regional Log Analytics workspace when any Azure Storage which is missing this diagnostic settings is created or updated.

## Try on Portal

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-policy%2Fmaster%2Fsamples%2FStorage%2Fdeploy-storage-monitoring-log-analytics%2Fblobservices%2Fazurepolicy.json)

## Try with PowerShell

```powershell
$definition = New-AzPolicyDefinition `
    -Name "deploy-storage-monitoring-log-analytics-blobs" `
    -DisplayName "Deploy Diagnostic Settings for Azure Storage blobs to Log Analytics workspace" `
    -Description "Deploys the diagnostic settings for Azure Storage blobs to stream to a regional Log Analytics workspace when any Azure Storage which is missing this diagnostic settings is created or updated." `
    -Policy 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Storage/deploy-storage-monitoring-log-analytics/blobservices/azurepolicy.rules.json' `
    -Parameter 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Storage/deploy-storage-monitoring-log-analytics/blobservices/azurepolicy.parameters.json' -Mode Indexed

$definition

$assignment = New-AzPolicyAssignment -Name <assignmentname> -Scope <scope>  -PolicyDefinition $definition

$assignment
```

## Try with CLI

```sh
az policy definition create \
    --name 'deploy-storage-monitoring-log-analytics-blobs' \
    --display-name 'Deploy Diagnostic Settings for Azure Storage blobs to Log Analytics workspace' \
    --description 'Deploys the diagnostic settings for Azure Storage blobs to stream to a regional Log Analytics workspace when any Azure Storage which is missing this diagnostic settings is created or updated.' \
    --rules 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Storage/deploy-storage-monitoring-log-analytics/blobservices/azurepolicy.rules.json' \
    --params 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Storage/deploy-storage-monitoring-log-analytics/blobservices/azurepolicy.parameters.json' \
    --mode Indexed

az policy assignment create --name <assignmentname> --scope <scope> --policy "deploy-storage-monitoring-log-analytics-blobs"
```
