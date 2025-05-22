#### Deploy the Azure AI Foundry resources using Bicep

```pwsh
# Create the Azure AI Foundry Hub
az deployment group create --resource-group Your_Resource_Group_Name --template-file main.bicep --parameters aiHubName=<unique_identifier>
```

This command may produce the following error:

```text
Code: ApiPropertiesInvalid
Message: The given 'apiProperties' 'statisticsEnabled' is invalid. Validation errors: Property 'statisticsEnabled' has not been defined and the schema does not allow additional properties. Path 'apiProperties.statisticsEnabled'.
```

##### Debugging Step
To capture the full debug output (including errors), redirect both stdout and stderr:

```bash
az deployment group create --resource-group itsarag2 --template-file main.bicep --parameters aiHubName=aiHubDoero2 --debug > error.txt 2>&1
```

For the complete error message, see [error.txt](error.txt).

#### Solution

Remove the following line from your Bicep files (such as `dependant-resources.bicep` and `docIntelligence.bicep`):

```bicep
statisticsEnabled: false
```

This property is not supported in the current API version and will cause the deployment to fail.