# durable-function-azurite
Sample repo for Azurite Issue. This issue is occuring on Mac 10 (High Sierra) using Visual Studio Code with Azurite Extension and Azure CLI. Pre requisite environment information is below, you may need to install azure cli tools via brew or npm

https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest

## Steps to replicate
1. Clone the repo and run `npm install` in the root folder
2. In Visual Studio Start Azurite via the VS Code Extension
3. Open console and run `func start`
4. Leave for a minute and you should be met with the following error. `The listener for function 'Functions.Hello' was unable to start.
[06/11/2019 10:25:34] The listener for function 'Functions.Hello' was unable to start. Microsoft.WindowsAzure.Storage: Connection refused. System.Net.Http: Connection refused. System.Private.CoreLib: Connection refused.`
5. Try to access the endpoint `http://localhost:7071/api/orchestrators/DurableFunctionsOrchestratorJS`

## Environment Information
```
Mac OS                            10.13.6
azurite                           3.2.0-preview (VS Code extension)
dotnet                            2.2.402

Azure Functions Core Tools (2.7.1846 Commit hash: 458c671341fda1c52bd46e1aa8943cb26e467830)
Function Runtime Version: 2.0.12858.0

azure-cli                         2.0.68 *

command-modules-nspkg               2.0.3
core                              2.0.68 *
nspkg                              3.0.4
telemetry                          1.0.3 *

Extensions:
interactive                        0.4.3

Python location '/usr/local/Cellar/azure-cli/2.0.68/libexec/bin/python'
Extensions directory '/Users/user/.azure/cliextensions'

Python (Darwin) 3.7.3 (default, Jun 19 2019, 07:40:15) 
[Clang 10.0.0 (clang-1000.11.45.5)]
```
