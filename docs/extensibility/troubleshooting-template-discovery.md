---
title: 針對 Visual Studio 中的範本探索進行疑難排解 |Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ebb7c49e5a8482ab0b2ef5c3a5257d0237b39c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836149"
---
# <a name="troubleshooting-template-installation"></a>疑難排解安裝的範本

如果您遇到問題，部署您的專案或項目範本時，您可以啟用診斷記錄。

1. 使用下列內容建立 pkgdef 檔案 Common7\IDE\CommonExtensions 資料夾中的安裝 (例如 C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef):

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. 藉由搜尋它，在 Windows 搜尋中，開啟安裝的 「 開發人員命令提示字元，然後執行`devenv /updateConfiguration`。

1. 啟動 Visual Studio，並啟動 [新增專案] 和 [新增項目] 對話方塊，來初始化兩個範本樹狀結構。 範本記錄現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** （對應至您的 Visual Studio 執行個體的安裝識別碼的執行個體識別碼）。 每個範本的樹狀目錄中初始化會將項目附加至這個記錄檔。

記錄檔包含下列資料行：

- **FullPathToTemplate**，其中包含下列值：

    - 1 代表資訊清單為基礎的部署

    - 0 代表磁碟為基礎的部署

- **TemplateFileName**

- 其他範本內容

> [!NOTE]
> 若要停用記錄，請移除 pkgdef 檔案，或變更的值`EnableTemplateDiscoveryLog`要`dword:00000000`，然後執行`devenv /updateConfiguration`一次。

## <a name="see-also"></a>另請參閱

[建立自訂專案和項目範本](creating-custom-project-and-item-templates.md)