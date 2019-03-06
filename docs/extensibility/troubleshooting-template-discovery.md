---
title: 針對 Visual Studio 中的範本探索進行疑難排解 |Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9ae6220ac38de7bf2edc7b5c305ecb377a46f18
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323996"
---
# <a name="troubleshooting-template-installation"></a>疑難排解安裝的範本

如果您遇到問題，部署您的專案或項目範本時，您可以啟用診斷記錄。

::: moniker range="vs-2017"

1. 建立在 pkgdef 檔案*Common7\IDE\CommonExtensions*為您的安裝資料夾。 例如， *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

::: moniker range=">=vs-2019"

1. 建立在 pkgdef 檔案*Common7\IDE\CommonExtensions*為您的安裝資料夾。 例如， *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

2. 將下列新增至 pkgdef 檔案：

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 開啟[開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)針對您的安裝和執行`devenv /updateConfiguration`。

::: moniker range="vs-2017"

4. 啟動 Visual Studio，並啟動 [新增專案] 和 [新增項目] 對話方塊，來初始化兩個範本樹狀結構。

   範本記錄現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** （對應至您的 Visual Studio 執行個體的安裝識別碼的執行個體識別碼）。 每個範本的樹狀目錄中初始化會將項目附加至這個記錄檔。

::: moniker-end

::: moniker range=">=vs-2019"

4. 啟動 Visual Studio，並啟動 [新增專案] 和 [新增項目] 對話方塊，來初始化兩個範本樹狀結構。

   範本記錄現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** （對應至您的 Visual Studio 執行個體的安裝識別碼的執行個體識別碼）。 每個範本的樹狀目錄中初始化會將項目附加至這個記錄檔。

::: moniker-end

記錄檔包含下列資料行：

- **FullPathToTemplate**，其中包含下列值：

    - 1 代表資訊清單為基礎的部署

    - 0 代表磁碟為基礎的部署

- **TemplateFileName**

- 其他範本內容

> [!NOTE]
> 若要停用記錄，請移除 pkgdef 檔案，或變更的值`EnableTemplateDiscoveryLog`要`dword:00000000`，然後執行`devenv /updateConfiguration`一次。

## <a name="see-also"></a>另請參閱

- [建立自訂專案和項目範本](creating-custom-project-and-item-templates.md)