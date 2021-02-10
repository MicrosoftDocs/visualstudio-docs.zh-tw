---
title: 用於偵測及管理 Visual Studio 執行個體的工具
titleSuffix: ''
description: 深入了解您可用來偵測及管理用戶端電腦上 Visual Studio 安裝的工具。
ms.date: 08/14/2017
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
ms.openlocfilehash: efd4091407d228a15cc80971d759e5371bddd3ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959255"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>用於偵測及管理 Visual Studio 執行個體的工具

有數個工具，您可以使用來偵測用戶端電腦上的 Visual Studio 安裝，以及管理安裝。

## <a name="detecting-existing-visual-studio-instances"></a>偵測現有的 Visual Studio 執行個體

我們提供許多工具來協助您偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體︰

* [vswhere](https://github.com/microsoft/vswhere)：內建于 Visual Studio 或可用於個別散發的可執行檔，可協助您尋找特定電腦上所有 Visual Studio 實例的位置。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)︰PowerShell 指令碼，使用安裝程式組態 API 來識別已安裝的 Visual Studio 執行個體。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：C# 和 C++ 範例，示範如何使用安裝程式組態 API 來查詢現有安裝。

此外，[安裝程式組態 API](<xref:Microsoft.VisualStudio.Setup.Configuration>) 還提供介面，讓想要建置其專屬公用程式的開發人員查閱 Visual Studio 執行個體。

## <a name="using-vswhereexe"></a>使用 vswhere.exe

`vswhere.exe` 會自動包含在 Visual Studio (從 Visual Studio 2017 15.2 版和更新版本) 開始，您也可以從 [[vswhere 版本] 頁面](https://github.com/Microsoft/vswhere/releases)下載。 使用 `vswhere -?` 來取得該工具的說明資訊。 作為範例，此命令會顯示 Visual Studio 的所有版本 (包括產品的較舊版本及發行前版本)，並以 JSON 格式輸出結果：

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
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

* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
