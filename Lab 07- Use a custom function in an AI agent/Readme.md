# Exercise

## Build an agent with custom tools

In this exercise, you’ll:

- Create a function for the agent to use  
- Define the function tools  
- Create the agent that uses the function tools  
- Send a message to the agent and process the response  
- Process function calls and display the agent’s response  

Start the exercise at:  
https://go.microsoft.com/fwlink/?linkid=2353623


-----------------

# Add Role: Cognitive Services Contributor

## Step 1: Authenticate PowerShell
```powershell
Connect-AzAccount -UseDeviceAuthentication
```

## Step 2: Define the Custom Role (Inline / Flattened Format)
```powershell
$role = @{
    Name = "CognitiveServicesAgentManager"
    Id = (New-Guid).Guid
    IsCustom = $true
    Description = "Custom role to allow full management of AIServices agents in Cognitive Services."
    Actions = @()
    NotActions = @()
    DataActions = @(
        "Microsoft.CognitiveServices/accounts/AIServices/agents/read",
        "Microsoft.CognitiveServices/accounts/AIServices/agents/write",
        "Microsoft.CognitiveServices/accounts/AIServices/agents/delete"
    )
    NotDataActions = @()
    AssignableScopes = @(
        "/subscriptions/<Subscription-id>"
    )
}
```

## Step 3: Create the Role
```powershell
New-AzRoleDefinition -Role $role
```

## Step 4: Look Up the User by UPN (Email Address)
> Use the `Id` value from the output as the ObjectId
```powershell
Get-AzADUser -UserPrincipalName "xxxxxxxx@LODSPRODMCA.onmicrosoft.com"
```

## Step 5: Get the Cognitive Services Account Name
> Look at the `Name` column in the output — this is your account name
```powershell
Get-AzCognitiveServicesAccount -ResourceGroupName "ResourceGroup1"
```

## Step 6: Assign the Role to the User || change the value of  <subscription-id> and <account-name> in below command
```powershell
New-AzRoleAssignment `
  -ObjectId "xxxxxxxxxxxxxxxxxxxxxxxx" `
  -RoleDefinitionName "CognitiveServicesAgentManager" `
  -Scope "/subscriptions/<subscription-id>/resourceGroups/ResourceGroup1/providers/Microsoft.CognitiveServices/accounts/<account-name>"
```




