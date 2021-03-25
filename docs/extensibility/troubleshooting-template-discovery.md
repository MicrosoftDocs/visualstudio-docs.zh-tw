---
title: 針對 Visual Studio 中的範本探索進行疑難排解 |Microsoft Docs
description: 瞭解如何啟用診斷記錄，以針對在 Visual Studio SDK 中部署自訂專案和範本進行疑難排解。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82b7b3f5eced4c8e24830fba34e47d224186949d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072945"
---
# <a name="troubleshooting-template-installation"></a>針對範本安裝進行疑難排解

如果您在部署專案或專案範本時遇到問題，您可以啟用診斷記錄。

::: moniker range="vs-2017"

1. 在 *Common7\IDE\CommonExtensions* 資料夾中建立 .pkgdef 檔案以供您安裝。 例如， *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 *Common7\IDE\CommonExtensions* 資料夾中建立 .pkgdef 檔案以供您安裝。 例如， *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*。

::: moniker-end

2. 將下列內容新增至 .pkgdef 檔案：

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 開啟安裝的 [開發人員命令提示字元](../ide/reference/command-prompt-powershell.md) ，然後執行 `devenv /updateConfiguration` 。

::: moniker range="vs-2017"

4. 開啟 Visual Studio，然後啟動 [新增專案] 和 [新增專案] 對話方塊，以初始化兩個範本樹狀結構。

   範本記錄檔現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_ [instanceid] 中 \VsTemplateDiagnosticsList.csv** (instanceid 對應至 Visual Studio) 實例的安裝識別碼。 每個範本樹狀結構初始化都會將專案附加至此記錄檔。

::: moniker-end

::: moniker range=">=vs-2019"

4. 開啟 Visual Studio 並啟動 [ **建立新專案** ] 和 [ **新專案** ] 對話方塊，以初始化兩個範本樹狀結構。

   範本記錄檔現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_ [instanceid] 中 \VsTemplateDiagnosticsList.csv** (instanceid 對應至 Visual Studio) 實例的安裝識別碼。 每個範本樹狀結構初始化都會將專案附加至此記錄檔。

::: moniker-end

記錄檔包含下列資料行：

- **FullPathToTemplate**，其值如下：

  - 1用於以資訊清單為基礎的部署

  - 0表示以磁片為基礎的部署

- **TemplateFileName**

- 其他範本屬性

> [!NOTE]
> 若要停用記錄，請移除 .pkgdef 檔案，或將的值變更 `EnableTemplateDiscoveryLog` 為 `dword:00000000` ，然後 `devenv /updateConfiguration` 再次執行。

## <a name="see-also"></a>另請參閱

- [建立自訂專案和專案範本](creating-custom-project-and-item-templates.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
