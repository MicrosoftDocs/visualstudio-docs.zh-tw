---
title: 針對 Visual Studio 中的範本探索進行疑難排解 |Microsoft Docs
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5225c741206e6a43ff024a5f184404f1ac2bc63
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904491"
---
# <a name="troubleshooting-template-installation"></a>疑難排解範本安裝

如果您在部署專案或專案範本時遇到問題，您可以啟用診斷記錄。

::: moniker range="vs-2017"

1. 在*Common7\IDE\CommonExtensions*資料夾中建立 .pkgdef 檔案，以供安裝之用。 例如， *C:\Program Files （x86） \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在*Common7\IDE\CommonExtensions*資料夾中建立 .pkgdef 檔案，以供安裝之用。 例如， *C:\Program Files （x86） \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

2. 將下列內容新增至 .pkgdef 檔案：

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 開啟安裝的[開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)，然後執行 `devenv /updateConfiguration` 。

::: moniker range="vs-2017"

4. 開啟 Visual Studio 並啟動 [新增專案] 和 [新增專案] 對話方塊，以初始化兩個範本樹狀結構。

   範本記錄現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_ [instanceid] \VsTemplateDiagnosticsList.csv** （instanceid 對應至 Visual Studio 實例的安裝識別碼）。 每個範本樹狀結構初始化都會將專案附加到此記錄檔。

::: moniker-end

::: moniker range=">=vs-2019"

4. 開啟 Visual Studio 並啟動 [**建立新專案**] 和 [**新增專案**] 對話方塊，以初始化兩個範本樹狀結構。

   範本記錄現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_ [instanceid] \VsTemplateDiagnosticsList.csv** （instanceid 對應至 Visual Studio 實例的安裝識別碼）。 每個範本樹狀結構初始化都會將專案附加到此記錄檔。

::: moniker-end

記錄檔包含下列資料行：

- **FullPathToTemplate**，其具有下列值：

  - 1用於以資訊清單為基礎的部署

  - 0用於以磁片為基礎的部署

- **TemplateFileName**

- 其他範本屬性

> [!NOTE]
> 若要停用記錄，請移除 .pkgdef 檔案，或將的值變更 `EnableTemplateDiscoveryLog` 為 `dword:00000000` ，然後 `devenv /updateConfiguration` 再次執行。

## <a name="see-also"></a>另請參閱

- [建立自訂專案和專案範本](creating-custom-project-and-item-templates.md)
