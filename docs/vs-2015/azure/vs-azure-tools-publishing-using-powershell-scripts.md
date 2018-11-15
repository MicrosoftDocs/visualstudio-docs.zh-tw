---
title: 使用 Windows PowerShell 指令碼來發行至開發和測試環境 |Microsoft Docs
description: 了解如何使用 Windows PowerShell 指令碼，從 Visual Studio 發佈至開發和測試環境。
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001872"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>使用 Windows PowerShell 指令碼來發佈開發與測試環境

當您在 Visual Studio 中建立 web 應用程式時，您可以產生您可以稍後使用來自動化以在 Azure App Service 或虛擬機器中的 Web 應用程式發行至 Azure 網站的 Windows PowerShell 指令碼。 您可以編輯和擴充以符合您的需求，Visual Studio 編輯器中的 Windows PowerShell 指令碼或指令碼整合到現有的組建、 測試和發佈指令碼。

使用這些指令碼，您可以佈建自訂您的網站，供暫時使用的版本 （也就是開發和測試環境）。 例如，您可能會設定您的網站的預備位置上執行測試套件、 重現錯誤、 測試錯誤修正、 試驗提議的變更，或設定示範或展示的自訂環境的網站或 Azure 虛擬機器上的特定版本。 您已建立的指令碼，將專案發佈之後，您可以重建相同環境重新執行指令碼，如有需要或您的 web 應用程式，以建立用於測試的自訂環境的自有組建執行指令碼。

## <a name="prerequisites"></a>必要條件

* Azure SDK 2.3 或更新版本。 請參閱[Visual Studio 下載](http://go.microsoft.com/fwlink/?LinkID=624384)。 （您不需要 Azure SDK 來產生 web 專案的指令碼。 這項功能僅供 web 專案，不在雲端服務中的 web 角色）。
* Azure PowerShell 0.7.4 或更新版本。 請參閱[如何安裝和設定 Azure PowerShell](/powershell/azure/overview)。
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175)或更新版本。

## <a name="additional-tools"></a>其他工具

可使用其他工具和適用於使用 Visual Studio 中的 PowerShell 進行 Azure 開發資源。 請參閱[PowerShell Tools for Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012)。

## <a name="generating-the-publish-scripts"></a>產生發佈指令碼

您可以產生發行指令碼虛擬機器裝載您的網站，當您建立新專案遵循[這些指示](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json)。 您也可以[產生的發行指令碼的 web 應用程式在 Azure App Service 中](/azure/app-service/scripts/app-service-powershell-deploy-github)。

## <a name="scripts-that-visual-studio-generates"></a>Visual Studio 產生的指令碼

Visual Studio 會產生名為解決方案層級資料夾**PublishScripts**包含兩個 Windows PowerShell 檔案，您的虛擬機器或網站，並包含您可以使用中的函式的模組的發行指令碼指令碼。 Visual Studio 也會產生指定您要部署之專案的詳細資料以 JSON 格式的檔案。

### <a name="windows-powershell-publish-script"></a>Windows PowerShell 發行指令碼

發行指令碼包含部署至網站或虛擬機器的特定發行步驟。 Visual Studio 提供語法著色適用於 Windows PowerShell 開發。 說明函式，而且您可以自由編輯指令碼，以符合您不斷變化的需求中的函式。

### <a name="windows-powershell-module"></a>Windows PowerShell 模組

Visual Studio 產生的 Windows PowerShell 模組包含發佈指令碼會使用的函式。 這些 Azure PowerShell 函式不打算進行修改。 請參閱[如何安裝和設定 Azure PowerShell](/powershell/azure/overview)。

### <a name="json-configuration-file"></a>JSON 組態檔

中建立 JSON 檔案**組態**資料夾和包含指定剛好要部署至 Azure 資源的組態資料。 Visual Studio 會產生檔案的名稱會是專案名稱-project-name-waws-dev.json 如果建立網站或專案名稱 VM dev.json 中，如果您建立虛擬機器。 以下是您建立網站時，會產生 JSON 組態檔的範例。 大部分的值都簡單易懂。 網站名稱是由 Azure 產生，因此它可能不符合您的專案名稱。

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

當您建立虛擬機器時，JSON 組態檔看起來如下所示。 雲端服務會建立為虛擬機器的容器。 虛擬機器包含透過 HTTP 和 HTTPS 進行 web 存取的常用端點以及 Web deploy，可讓您從本機電腦、 遠端桌面和 Windows PowerShell 發佈至網站的端點。

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

您可以編輯 JSON 組態以變更執行發佈指令碼時，會發生什麼事。 `cloudService`並`virtualMachine`區段都是必要的但您可以刪除`databases`區段如果您不需要它。 Visual Studio 會產生預設組態檔中的空白屬性是選擇性的;需要這些屬性的值在預設組態檔。

如果您有多個部署環境 （稱為位置） 的網站，而不是在 Azure 中的單一生產網站，您可以在 JSON 組態檔中包含位置名稱，該網站的名稱。 例如，如果您有網站，稱為**mysite**和名為位置**測試**則 URI 為`mysite-test.cloudapp.net`，但要使用組態檔中的正確名稱是 mysite （test）。 您可以只執行此網站和位置存在於您的訂用帳戶。 如果不存在，請建立網站執行指令碼不指定位置，然後建立的插槽[Azure 入口網站](https://portal.azure.com/)，之後再以修改過的網站名稱執行指令碼。 如需 web 應用程式的部署位置的詳細資訊，請參閱[設定預備環境中 Azure App Service 的 web apps](/azure/app-service/web-sites-staged-publishing)。

## <a name="how-to-run-the-publish-scripts"></a>如何執行發佈指令碼

如果您從未執行過 Windows PowerShell 指令碼之前，您必須先設定執行原則以啟用要執行的指令碼。 原則是安全性功能可防止使用者執行 Windows PowerShell 指令碼，如果它們容易受到惡意程式碼或病毒威脅執行指令碼。

### <a name="run-the-script"></a>執行指令碼

1. 建立您的專案的 Web Deploy 封裝。 Web Deploy 套件是經過壓縮的封存 （.zip 檔案），其中包含您想要複製到您的網站或虛擬機器的檔案。 您可以在任何 web 應用程式，在 Visual Studio 中建立 Web Deploy 封裝。

   ![建立 Web 部署套件](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   如需詳細資訊，請參閱 <<c0> [ 如何： 在 Visual Studio 中建立 Web 部署套件](https://msdn.microsoft.com/library/dd465323.aspx)。 您也可以自動建立 Web Deploy 封裝，，如中所述[自訂和擴充發佈指令碼](#customizing-and-extending-publish-scripts)。

1. 在 **方案總管**，開啟 指令碼的操作功能表，然後選擇**以 PowerShell ISE 開啟**。
1. 如果此電腦上執行 Windows PowerShell 指令碼，第一次，以系統管理員權限開啟命令提示字元 視窗，並輸入下列命令：

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. 使用下列命令登入 Azure。

    ```powershell
    Add-AzureAccount
    ```

    出現提示時，提供您的使用者名稱和密碼。

    請注意當您自動執行指令碼，這個提供 Azure 認證的方法無法運作。 因此，您應該改用`.publishsettings`檔案來提供認證。 一次，您使用命令**Get-azurepublishsettingsfile**若要從 Azure 下載檔案，然後之後使用**Import-azurepublishsettingsfile**匯入檔案。 如需詳細指示，請參閱 <<c0> [ 如何安裝和設定 Azure PowerShell](/powershell/azure/overview)。

1. （選擇性）資料庫和網站，而不要發佈您的 web 應用程式，如果您想要建立 Azure 資源，例如虛擬機器，使用**Publish-WebApplication.ps1**命令搭配 **-組態**引數設定為 JSON 組態檔。 此命令列使用 JSON 組態檔來決定要建立哪些資源。 因為它會使用預設設定的其他命令列引數，它會建立資源，但不會發佈您的 web 應用程式。 – Verbose 選項會提供有關最新動態的詳細資訊。

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. 使用**Publish-WebApplication.ps1**命令，其中一種叫用指令碼和發行您的 web 應用程式的下列範例所示。 如果您需要覆寫任何其他引數，例如訂用帳戶名稱的預設設定、 發佈封裝名稱、 虛擬機器認證或資料庫伺服器認證，您可以指定這些參數。 使用 **– Verbose**選項，以查看發行程序進度的詳細資訊。

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    如果您打算建立虛擬機器，命令看起來會如下所示。 此範例也示範如何指定多個資料庫的認證。 針對這些指令碼建立的虛擬機器，SSL 憑證不是來自受信任的根授權單位。 因此，您需要使用 **– AllowUntrusted**選項。

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    指令碼可以建立資料庫，但不會建立資料庫伺服器。 如果您想要建立資料庫伺服器，您可以使用**New-azuresqldatabaseserver** Azure 模組中的函式。

## <a name="customizing-and-extending-the-publish-scripts"></a>自訂和擴充發佈指令碼

您可以自訂發佈指令碼和 JSON 組態檔。 Windows PowerShell 模組中的函式**AzureWebAppPublishModule.psm1**不適合修改。 如果您只想要指定不同的資料庫或變更某些虛擬機器的內容，編輯 JSON 組態檔。 如果您想要擴充指令碼，以自動建置和測試專案的功能，您可以實作中的函式 stub **Publish-WebApplication.ps1**。

若要自動建置您的專案，將呼叫 MSBuild 的程式碼加入`New-WebDeployPackage`這個程式碼範例所示。 MSBuild 命令的路徑是您已安裝的 Visual Studio 版本而有所不同。 若要取得正確的路徑，您可以使用此函式**Get-msbuildcmd**，在此範例中所示。

### <a name="to-automate-building-your-project"></a>若要自動建置您的專案

1. 新增`$ProjectFile`全域參數區段中的參數。

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copy 函式`Get-MSBuildCmd`到您的指令碼檔案。

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. 取代`New-WebDeployPackage`使用下列程式碼，並取代預留位置線條建構`$msbuildCmd`。 此程式碼是 Visual Studio 2015。 如果您使用 Visual Studio 2017，變更**VisualStudioVersion**屬性設`15.0`(`12.0`適用於 Visual Studio 2013)。

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    若要建置您的 web 應用程式，使用 MsBuild.exe。 如需說明，請參閱 MSBuild 命令列參考： [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>開始執行建置命令

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. 呼叫`New-WebDeployPackage`這一行的前面的函式： `$Config = Read-ConfigFile $Configuration` web 應用程式或`$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)`適用於虛擬機器。

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. 叫用自訂指令碼，從命令列使用傳遞`$Project`引數，如下列範例所示：

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    若要自動測試您的應用程式，將程式碼加入`Test-WebApplication`。 請務必在行取消註解**Publish-WebApplication.ps1**呼叫這些函數。 如果您沒有提供實作，您可以手動建立您的專案使用 Visual Studio，然後再執行 發行指令碼發行至 Azure。

## <a name="publishing-function-summary"></a>發佈函式摘要
若要取得您可以使用 Windows PowerShell 命令提示字元函式的說明，請使用命令`Get-Help function-name`。 說明包含參數說明和範例。 指令碼原始程式檔中也有相同的說明文字**AzureWebAppPublishModule.psm1**並**Publish-WebApplication.ps1**。 指令碼和說明會在您的 Visual Studio 語言當地語系化。

**AzureWebAppPublishModule**

| 函式名稱 | 描述 |
| --- | --- |
| 新增 AzureSQLDatabase |建立新的 Azure SQL database。 |
| Add-azuresqldatabases |從 Visual Studio 會產生 JSON 組態檔中的值建立 Azure SQL database。 |
| Add-azurevm |建立 Azure 虛擬機器並傳回所部署 VM 的 URL。 此函式會設定先決條件，然後呼叫**New-azurevm**函式 （Azure 模組） 來建立新的虛擬機器。 |
| Add-azurevmendpoints |將新的輸入的端點加入至虛擬機器，並傳回含有新端點的虛擬機器。 |
| Add-azurevmstorage |目前的訂用帳戶中建立新的 Azure 儲存體帳戶。 帳戶的名稱開頭為"devtest"後面接著唯一的英數字元字串。 函數會傳回新的儲存體帳戶的名稱。 指定的位置或同質群組的新的儲存體帳戶。 |
| Add-azurewebsite |具有指定的名稱和位置建立網站。 此函式會呼叫**New-azurewebsite** Azure 模組中的函式。 如果訂用帳戶已不包含具有指定名稱的網站，此函式會建立該網站，並傳回網站物件。 否則它會傳回 `$null`。 |
| 備份訂用帳戶 |儲存目前的 Azure 訂用帳戶中`$Script:originalSubscription`變數在指令碼範圍。 此函式會儲存目前的 Azure 訂用帳戶 (由`Get-AzureSubscription -Current`) 和與其儲存體帳戶，以及此指令碼所變更的訂用帳戶 (儲存在變數`$UserSpecifiedSubscription`) 與其儲存體帳戶，在指令碼範圍。 儲存這些值，您可以使用函式，例如`Restore-Subscription`、 原始的目前訂用帳戶和儲存體帳戶還原為目前的狀態，如果目前的狀態已變更。 |
| Find-azurevm |取得指定的 Azure 虛擬機器。 |
| Format-devtestmessagewithtime |前面加上的日期和時間的訊息。 此函式專為寫入 Error 和 Verbose 串流的訊息。 |
| 取得 AzureSQLDatabaseConnectionString |組合連接字串來連接到 Azure SQL database。 |
| Get-azurevmstorage |傳回了名稱模式的第一個儲存體帳戶名稱"devtest *"（區分大小寫） 中指定的位置或同質群組。如果"devtest*」 儲存體帳戶不符合位置或同質群組、 函式會忽略它。 指定的位置或同質群組。 |
| Get-msdeploycmd |傳回執行 MsDeploy.exe 工具的命令。 |
| New-azurevmenvironment |尋找或建立虛擬機器中的 JSON 組態檔中的值相符的訂用帳戶。 |
| Publish-webpackage |使用 MsDeploy.exe 和 web 發行套件。將資源部署至網站的 zip 檔案。 此函式不會產生任何輸出。 如果呼叫 MSDeploy.exe 失敗，此函式會擲回例外狀況。 若要取得更詳細的輸出，請使用 **-Verbose**選項。 |
| Publish-webpackagetovm |驗證參數值，然後再撥打**Publish-webpackage**函式。 |
| 讀取-ConfigFile |驗證 JSON 組態檔，並傳回所選值的雜湊表。 |
| 還原-訂用帳戶 |將目前的訂用帳戶重設原始的訂用帳戶中。 |
| Test-azuremodule |傳回`$true`如果安裝的 Azure 模組版本為 0.7.4 或更新版本。 傳回`$false`如果尚未安裝模組，或是為舊的版本。 此函式沒有任何參數。 |
| 測試 AzureModuleVersion |傳回`$true`如果 Azure 模組版本為 0.7.4 或更新版本。 傳回`$false`如果尚未安裝模組，或是為舊的版本。 此函式沒有任何參數。 |
| 測試 HttpsUrl |將輸入的 URL 轉換為 System.Uri 物件。 傳回`$True`如果 URL 為絕對值，而且其配置為 https。 傳回`$false`如果 URL 是相對值、 其配置不是 HTTPS，或輸入的字串無法轉換成 URL。 |
| 測試成員 |傳回`$true`如果屬性或方法是物件的成員。 否則傳回 `$false`。 |
| 寫入 ErrorWithTime |寫入前面加上目前時間的錯誤訊息。 此函式會呼叫**Format-devtestmessagewithtime**函式前面加上訊息寫入 Error 串流之前的時間。 |
| 寫入 HostWithTime |將訊息寫入主機程式 (**Write-host**) 前面加上目前的時間。 寫入主機程式的影響而有所不同。 大部分程式裝載 Windows PowerShell 這些訊息寫入標準輸出。 |
| 寫入 VerboseWithTime |寫入前面加上目前時間的詳細資訊訊息。 因為它會呼叫**Write-verbose**，訊息會顯示只有當執行指令碼**Verbose**參數或當**VerbosePreference**喜好設定設為**繼續**。 |

**發行 WebApplication**

| 函式名稱 | 描述 |
| --- | --- |
| 新 AzureWebApplicationEnvironment |建立 Azure 資源，例如網站或虛擬機器。 |
| 新 WebDeployPackage |此函式未實作。 您可以在此函式來建置您的專案中加入命令。 |
| 發行 AzureWebApplication |發行至 Azure web 應用程式。 |
| 發行 WebApplication |建立及部署 Web 應用程式、 虛擬機器、 SQL database 和 Visual Studio web 專案的儲存體帳戶。 |
| 測試 WebApplication |此函式未實作。 您可以新增命令中此函式來測試您的應用程式。 |

## <a name="next-steps"></a>後續步驟
深入了解 PowerShell 指令碼，請閱讀[使用 Windows PowerShell 撰寫指令碼](https://technet.microsoft.com/library/bb978526.aspx)並查看其他 Azure PowerShell 指令碼，於[指令碼中心](https://azure.microsoft.com/documentation/scripts/)。
