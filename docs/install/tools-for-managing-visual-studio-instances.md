---
title: "用於偵測及管理 Visual Studio 執行個體的工具 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 2f53d41f0501f5fb314b3235540edb4344b9cf7d
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>用於偵測及管理 Visual Studio 執行個體的工具

## <a name="detecting-existing-visual-studio-instances"></a>偵測現有的 Visual Studio 執行個體
我們提供數種工具來協助您偵測及管理用戶端電腦上已安裝的 Visual Studio 執行個體︰

* [VSWhere](https://github.com/microsoft/vswhere) \(英文\)：這個內建於 Visual Studio 中，也可供個別發佈的可執行檔，可以協助您在特定電腦上找到所有 Visual Studio 執行個體的位置。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)︰PowerShell 指令碼，使用安裝程式組態 API 來識別已安裝的 Visual Studio 執行個體。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：C# 和 C++ 範例，示範如何使用安裝程式組態 API 來查詢現有安裝。

此外，[安裝程式組態 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) 還提供介面，讓想要建置其專屬公用程式的開發人員查閱 Visual Studio 執行個體。

## <a name="using-vswhereexe"></a>使用 vswhere.exe
`vswhere.exe` 會自動包含在 Visual Studio 2017 15.2 版或更新版本之中，您也可以從它的[版本頁面](https://github.com/Microsoft/vswhere/releases) \(英文\) 下載它。 使用 `vswhere -?` 來取得該工具的說明資訊。 作為範例，此命令會顯示 Visual Studio 的所有版本 (包括產品的較舊版本及發行前版本)，並以 JSON 格式輸出結果：

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>如需 Visual Studio 2017 安裝的詳細資訊，請參閱 [Heath Stewart's blog articles](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) (Heath Stewart 的部落格文章)。


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>編輯 Visual Studio 執行個體的登錄
在 Visual Studio 2017 中，登錄設定會儲存在私人位置，這可在相同電腦上啟用相同版本之 Visual Studio 的多個並存執行個體。

因為這些項目不是儲存在全域登錄中，針對使用登錄編輯程式來變更登錄設定有一些特殊指示︰

1. 如果您有開啟的 Visual Studio 2017 執行個體，請將它關閉。
2. 啟動 `regedit.exe`。
3. 選取 `HKEY_LOCAL_MACHINE` 節點。
4. 從 Regedit 主功能表選取 [檔案] -> [載入登錄區]，然後選取私人登錄檔 (儲存在 **AppData\Local** 資料夾中)。 例如: 
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` 對應至您想要瀏覽的 Visual Studio 執行個體。

系統將會提示您提供登錄區名稱，這會變成您的已隔離登錄區的名稱。 這麼做之後，您應該能在您所建立的已隔離登錄區下瀏覽登錄。

> [!IMPORTANT]
> 在重新啟動 Visual Studio 之前，必須卸載您所建立的已隔離登錄區。 若要這樣做，從 Regedit 主功能表選取 [檔案] -> [解除載入登錄區] (如果您沒有這麼做，則檔案會維持鎖定且 Visual Studio 將無法啟動)。

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面，以取得疑難排解祕訣。 同樣地，您可以透過 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具向我們報告產品問題，或者在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享建議。 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。 您也可以透過我們在 [Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動 (需要 [GitHub](https://github.com/) 帳戶)。
