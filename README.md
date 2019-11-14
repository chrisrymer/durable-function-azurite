# durable-function-azurite
Sample repo for Azurite Issue. This issue is occuring on Mac 10 (High Sierra) using Visual Studio Code with Azurite Extension and Azure CLI. Pre requisite environment information is below, you may need to install azure cli tools via brew or npm

https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest

## Steps to replicate
1. Clone the repo and run `npm install` in the root folder
2. In Visual Studio Start Azurite via the VS Code Extension
3. OPen the terminal and Install the Azure CLI `npm install -g azure-functions-core-tools`
4. Open console and run `func start`
5. Leave for a minute and you should be met with the following error. `The listener for function 'Functions.Hello' was unable to start.
[06/11/2019 10:25:34] The listener for function 'Functions.Hello' was unable to start. Microsoft.WindowsAzure.Storage: Connection refused. System.Net.Http: Connection refused. System.Private.CoreLib: Connection refused.`
5. Try to access the endpoint `http://localhost:7071/api/orchestrators/DurableFunctionsOrchestratorJS`

_After upgrading azure-cli step 4  now quits the function app after the following error_

```
[06/11/2019 10:42:59] A host error has occurred during startup operation 'e18a940b-4851-4c6a-a832-10b08eb53352'.
[06/11/2019 10:42:59] Microsoft.WindowsAzure.Storage: cannotconnect.
```

## UPDATE
I have just update to the latest `azure-cli` client and I am now receiving a new error. I did feel that maybe the app was struggling to connect on the loopback ip `127.0.0.1`. We have some crazy proxy restrictions but generally local dev is fine. I have checked and `127.0.0.1` is fine.

```
A host error has occurred during startup operation 'e18a940b-4851-4c6a-a832-10b08eb53352'.
[06/11/2019 10:42:59] Microsoft.WindowsAzure.Storage: cannotconnect.
Value cannot be null.
Parameter name: provider
```

## Environment Information
```
Mac OS                            10.13.6
azurite                           3.2.0-preview (VS Code extension)
dotnet                            2.2.402

Azure Functions Core Tools (2.7.1846 Commit hash: 458c671341fda1c52bd46e1aa8943cb26e467830)
Function Runtime Version: 2.0.12858.0

azure-cli                         2.0.75 *

command-modules-nspkg              2.0.3
core                              2.0.75 *
nspkg                              3.0.4
telemetry                          1.0.4

Extensions:
interactive                        0.4.3

Python location '/usr/local/Cellar/azure-cli/2.0.75/libexec/bin/python'
Extensions directory '/Users/user/.azure/cliextensions'

Python (Darwin) 3.7.5 (default, Nov  1 2019, 02:16:38) 
[Clang 10.0.0 (clang-1000.11.45.5)]
```
