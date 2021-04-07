---
title: 用於偵測及管理 Visual Studio 執行個體的工具
titleSuffix: ''
description: 深入了解您可用來偵測及管理用戶端電腦上 Visual Studio 安裝的工具。
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b6b641081c9b969cadd2c9517967adb8cc4cb1e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547436"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>用於偵測及管理 Visual Studio 執行個體的工具

您可以使用數個工具來偵測用戶端電腦上的 Visual Studio 安裝，以及管理安裝。

## <a name="detecting-existing-visual-studio-instances"></a>偵測現有的 Visual Studio 執行個體

下列工具和公用程式可協助您偵測和管理用戶端電腦上已安裝的 Visual Studio 實例：

* [**vswhere**](https://github.com/microsoft/vswhere)：內建于 Visual Studio 或可用於個別散發的可執行檔，可協助您尋找特定電腦上所有 Visual Studio 實例的位置。
* [**Vssetup.powershell**](https://github.com/microsoft/vssetup.powershell)： powershell 腳本，使用安裝設定 API 來識別 Visual Studio 的已安裝實例。
* [**VS-設定-範例**](https://github.com/microsoft/vs-setup-samples)： c # 和 c + + 範例，示範如何使用安裝程式設定 API 來查詢現有安裝。
* [**Windows Management Instrumentation (WMI)**](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page)：可透過 Visual Studio 類別 MSFT_VSInstance 查詢 Visual Studio 實例資訊。 
* [**安裝程式設定 API**](<xref:Microsoft.VisualStudio.Setup.Configuration>)提供的介面可供開發人員想要為詢問 Visual Studio 實例建立自己的公用程式。
* [**Microsoft Endpoint Configuration Manager 軟體清查**](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory)：可以用來收集用戶端裝置上 Visual Studio 實例的相關資訊。 

## <a name="using-vswhereexe"></a>使用 vswhere.exe

`vswhere.exe` 會自動包含在 Visual Studio 2017 和更新版本中，或者您可以從 [[vswhere 版本] 頁面](https://github.com/Microsoft/vswhere/releases)下載。 使用 `vswhere -?` 來取得該工具的說明資訊。 例如，此命令會顯示 Visual Studio 的所有版本（包括舊版的產品和發行前版本），並以 JSON 格式輸出結果：

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>使用 Windows Management Instrumentation (WMI) 

如果電腦上已安裝 Visual Studio 用戶端偵測器公用程式，您可以使用 WMI 查詢 Visual Studio 的實例資訊。 Visual Studio 用戶端偵測器公用程式預設會隨每個 Visual Studio 2017 和 Visual Studio 2019 更新（在2020年5月12日或之後發行）進行安裝。 如果您想要獨立安裝，也可以在 [Microsoft Update 目錄](https://catalog.update.microsoft.com/) 中取得。  如需如何使用公用程式傳回 Visual Studio 實例資訊的範例，請在用戶端電腦上以系統管理員身分開啟 PowerShell，然後輸入下列命令：

```cmd
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>使用 Microsoft Endpoint Configuration Manager 

[Microsoft Endpoint Configuration Manager 軟體清查](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) 功能可以用來查詢和收集用戶端裝置上 Visual Studio 實例的相關資訊。 例如，下列查詢會針對所有已安裝的 Visual Studio 2017 和2019實例，傳回 Visual Studio 安裝所在的顯示名稱、版本和裝置名稱： 

```WQL 
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
``` 

::: moniker range="vs-2017"

> [!TIP]
> 如需 Visual Studio 2017 安裝的詳細資訊，請參閱 [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Visual Studio 安裝封存)。

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>編輯 Visual Studio 執行個體的登錄

在 Visual Studio 中，登錄設定會儲存在私人位置，這可在相同電腦上啟用 Visual Studio 相同版本的多個並存執行個體。

因為這些項目不是儲存在全域登錄中，針對使用登錄編輯程式來變更登錄設定有一些特殊指示︰

1. 如果您有開啟的 Visual Studio 執行個體，請將其關閉。

1. 啟動 `regedit.exe`。

1. 選取 `HKEY_LOCAL_MACHINE` 節點。

1. 從 Regedit 主功能表選取 [檔案  >  **載入 Hive ...** ]，然後選取私人登錄檔（儲存在 **AppData\Local** 資料夾中）。 例如：

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` 對應至您想要瀏覽的 Visual Studio 執行個體。

系統將會提示您提供登錄區名稱，這會變成您的已隔離登錄區的名稱。 這麼做之後，您應該能在您所建立的已隔離登錄區下瀏覽登錄。

> [!IMPORTANT]
> 在重新啟動 Visual Studio 之前，必須卸載您所建立的已隔離登錄區。 若要這樣做，**請**  >  從 Regedit 主功能表選取 [檔案卸載 **Hive** ]。 (如果您沒有這麼做，則檔案會維持鎖定且 Visual Studio 將無法啟動)。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)
