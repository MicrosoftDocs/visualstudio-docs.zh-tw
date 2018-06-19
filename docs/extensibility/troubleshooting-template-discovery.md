---
title: 疑難排解 Visual Studio 中的範本探索 |Microsoft 文件
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136724"
---
# <a name="troubleshooting-template-installation"></a>範本安裝疑難排解

如果您執行部署您的專案或項目範本的問題，您可以啟用診斷記錄。

1. 建立 Common7\IDE\CommonExtensions 資料夾中的 pkgdef 檔案安裝 (例如 C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) 具有下列內容：

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. 藉由搜尋它，在 Windows 搜尋中，開啟安裝的 「 開發人員命令提示字元，然後執行`devenv /updateConfiguration`。

1. 啟動 Visual Studio，然後啟動新的專案和新的項目對話方塊，來初始化兩個範本樹狀結構。 範本記錄現在會出現在 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** （執行個體識別碼對應至您的 Visual Studio 執行個體的安裝識別碼）。 每個範本樹狀目錄中初始化會將項目附加至這個記錄檔。

記錄檔包含下列資料行：

- **FullPathToTemplate**，其中包含下列值：

    - 1 代表資訊清單為基礎的部署

    - 0 代表磁碟為基礎的部署

- **TemplateFileName**

- 其他範本的內容

> [!NOTE]
> 若要停用記錄，請移除該 pkgdef 檔案，或變更的值`EnableTemplateDiscoveryLog`至`dword:00000000`，然後執行`devenv /updateConfiguration`一次。

## <a name="see-also"></a>另請參閱

[建立自訂專案與項目範本](creating-custom-project-and-item-templates.md)