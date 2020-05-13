---
title: 在可視化工作室中排除範本發現 |微軟文件
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698926"
---
# <a name="troubleshooting-template-installation"></a>容錯排除樣本安裝

如果在部署專案或專案範本時遇到問題,可以啟用診斷日誌記錄。

::: moniker range="vs-2017"

1. 在*公用 7_IDE_公用擴展資料夾中*為安裝創建 pkgdef 檔案。 例如 *,C:_程式檔 (x86)\微軟可視化工作室\2017_企業_通用7_IDE_通用擴展\啟用PkgDef_pkgdef*。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在*公用 7_IDE_公用擴展資料夾中*為安裝創建 pkgdef 檔案。 例如 *,C:_程式檔 (x86)\微軟可視化工作室\2019_企業_通用7_IDE_通用擴展\啟用PkgDef_pkgdef*。

::: moniker-end

2. 將以下內容加入到 pkgdef 檔案:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 打開安裝並運行`devenv /updateConfiguration`的[開發人員命令提示。](/dotnet/framework/tools/developer-command-prompt-for-vs)

::: moniker range="vs-2017"

4. 打開可視化工作室並啟動"新專案"和"新專案"對話框,以初始化兩個範本樹。

   樣本紀錄現在以 **%LOCALAPPDATA%*Microsoft_VisualStudio_15.0_[實例id]\VsTemplate診斷清單.csv(** 實例id對應於可視化工作室實例的安裝 ID) 中顯示。 每個範本樹初始化都會將條目追加到此日誌。

::: moniker-end

::: moniker range=">=vs-2019"

4. 打開視覺化工作室並啟動 **「創建新專案和****新專案」** 對話方塊,以初始化兩個樣本樹。

   樣本紀錄現在以 **%LOCALAPPDATA%*Microsoft_VisualStudio_16.0_[實例id]\VsTemplate診斷清單.csv(** 實例id對應於可視化工作室實例的安裝 ID) 中顯示。 每個範本樹初始化都會將條目追加到此日誌。

::: moniker-end

紀錄檔包含以下欄位:

- **FullPathtoTemplate**, 具有以下值:

  - 1 表示基於清單的部署

  - 0 表示基於磁碟的部署

- **樣本檔案名稱**

- 其他樣本屬性

> [!NOTE]
> 要關閉紀錄記錄,請刪除 pkgdef 檔,或將的值`EnableTemplateDiscoveryLog`更改為`dword:00000000`,然後再次`devenv /updateConfiguration`執行。

## <a name="see-also"></a>另請參閱

- [建立自訂項目與專案樣本](creating-custom-project-and-item-templates.md)
