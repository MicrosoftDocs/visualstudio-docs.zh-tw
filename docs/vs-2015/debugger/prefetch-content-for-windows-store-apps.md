---
title: 預先擷取 Windows 市集應用程式的內容 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b7d8b859efa5fac2e3643f4d3a0bd694cd2edd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940596"
---
# <a name="prefetch-content-for-windows-store-apps"></a>預先擷取 Windows 市集應用程式的內容
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

僅適用於 Windows] (../Image/windows_only_content.png"windows_only_content")  
  
 若要讓 Windows 市集應用程式回應速度更快，您可以要求預先部分網頁內容，例如網頁或影像載入至應用程式的 Windows [WinINet](http://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)快取。 這項功能稱為預先擷取。 如果是啟動時會用到的內容，這種方式就特別有效。但是，您也可以預先擷取其他經常用到的內容。 [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) 類別的方法可讓您指定預先載入內容的 URI。 如需如何將 ContentPrefetcher 功能新增至應用程式的範例，請參閱 Windows SDK 的[內容預先擷取範例](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)。  
  
 Windows 會使用啟發學習法，判斷預先擷取的發生時機、是否要預先擷取以及要下載的資源。 啟發學習法會將系統網路和電源狀況、使用者應用程式使用歷程記錄，以及先前嘗試預先擷取的結果都納入考量。 在 Visual Studio 中，您可以使用 [觸發 Microsoft Store 應用程式預先擷取] 命令強制 Windows 忽略 ContentPrefetcher 啟發學習法並預先載入所有指定的 Web 內容。 如果您要測試應用程式的行為或效能，並且要在已知的狀態 (已載入或未載入) 下預先擷取內容，這個命令就很有用。  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>若要強制 ContentPrefetcher 預先載入指定的資源  
 下列程序會假設您已經設定 ContentPrefetcher 功能，而且已指定要在應用程式專案中預先載入的內容 URI。 如果指定的資源是新資源或已經過修改，則您必須先啟動並停止應用程式，再選擇 [觸發 Microsoft Store 應用程式預先擷取] 命令，才能強制預先載入內容。 您要先執行應用程式以註冊 URI。 接著，[觸發 Microsoft Store 應用程式預先擷取] 命令會強制 ContentPrefetcher 下載內容並將其新增至快取。 未來執行應用程式時，您就可以認定內容已經預先載入。  
  
1. 啟動應用程式，向應用程式註冊預先擷取內容 URI。 在 [偵錯] 功能表上選擇 [開始偵錯] (鍵盤快速鍵：F5)。  
  
2. 在 **偵錯**功能表上，選擇**停止偵錯**(鍵盤快速鍵：Shift + F5）。  
  
3. 在 [偵錯] 功能表上選擇 [其他偵錯目標]，然後選擇 [觸發 Microsoft Store 應用程式預先擷取]。  
  
   現在您可以在已經預先擷取 Web 資源的情況下偵錯、測試或分析應用程式。  
  
> [!NOTE]
>  當您新增或修改指定的 Web 內容時，請重複上述步驟。  
  
## <a name="see-also"></a>另請參閱  
 [部落格文章：在 Visual Studio 2013 Update 2 中的 Windows 市集應用程式中觸發預先擷取](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)
