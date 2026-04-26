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

add : Cognitive Services Contributor
#Step1 : Authenticate powershell
Connect-AzAccount -UseDeviceAuthentication

#Step 2 : Define the custom role inline (flattened format)
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
        "/subscriptions/<Subscription -id>"
    )
}

#Step 3 :  Create the role
New-AzRoleDefinition -Role $role

#Step 4 :  Look up the user by UPN (email address) , for object id
# Use the "id" column value for object id
Get-AzADUser -UserPrincipalName "xxxxxxxx@LODSPRODMCA.onmicrosoft.com"



#Step 4 :Get the Account name : Look at the "Name" column in the output — that’s the "account name" you need.
Get-AzCognitiveServicesAccount -ResourceGroupName ResourceGroup1

# Assign the role to your user
New-AzRoleAssignment `
  -ObjectId xxxxxxxxxxxxxxxxxxxxxxxx `
  -RoleDefinitionName "CognitiveServicesAgentManager" `
  -Scope "/subscriptions/<subscription-id>/resourceGroups/<your-resource-group>/providers/Microsoft.CognitiveServices/accounts/<account-name>"





