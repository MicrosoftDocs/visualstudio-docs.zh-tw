---
title: 使用預先擷取的內容在 UWP 應用程式進行偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 241937c8462577d6af375d2440efe828a738a8cc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475920"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>偵錯使用 Visual Studio 中的預先擷取的內容的 UWP 應用程式
  
 若要讓 UWP 應用程式更能有效回應，您可以要求 Windows 將在應用程式預先載入某些 web 內容，例如網頁或影像[WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c)快取。 這項功能稱為預先擷取。 它是特別為啟動時所使用的內容有效，但可以預先擷取其他經常使用的內容太。 方法的[Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher)類別可讓您指定您想要預先載入內容 Uri。 請參閱 Windows SDK[內容預先擷取範例](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)如需如何將 ContentPrefetcher 功能加入至您的應用程式的範例。  
  
 Windows 會使用啟發學習法，判斷預先擷取的發生時機、是否要預先擷取以及要下載的資源。 啟發學習法會將系統網路和電源狀況、使用者應用程式使用歷程記錄，以及先前嘗試預先擷取的結果都納入考量。 在 Visual Studio 中，您可以使用**觸發 Windows 市集應用程式預先擷取**命令強制 Windows 忽略 ContentPrefetcher 啟發學習法並預先載入所有指定的 web 內容。 如果您要測試應用程式的行為或效能，並且要在已知的狀態 (已載入或未載入) 下預先擷取內容，這個命令就很有用。  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>若要強制 ContentPrefetcher 預先載入指定的資源  
 下列程序會假設您已經設定 ContentPrefetcher 功能，而且已指定要在應用程式專案中預先載入的內容 URI。 若要新增或修改指定的資源時，強制預先載入內容，您必須先啟動然後停止應用程式，再選擇**觸發 Windows 市集應用程式預先擷取**命令。 您要先執行應用程式以註冊 URI。 **觸發 Windows 市集應用程式預先擷取**命令會強制 ContentPrefetcher 下載內容，並將它加入快取。 未來執行應用程式時，您就可以認定內容已經預先載入。  
  
1.  啟動應用程式，向應用程式註冊預先擷取內容 URI。 在**偵錯**功能表上，選擇**開始偵錯**(快速鍵： F5)。  
  
2.  在**偵錯**功能表上，選擇**停止偵錯**(快速鍵： Shift + F5)。  
  
3.  在**偵錯**功能表上，選擇**其他偵錯目標**，然後選擇 **觸發 Windows 市集應用程式預先擷取**。  
  
 現在您可以在已經預先擷取 Web 資源的情況下偵錯、測試或分析應用程式。  
  
> [!NOTE]
>  當您新增或修改指定的 Web 內容時，請重複上述步驟。  
  
## <a name="see-also"></a>另請參閱  
 [部落格文章： 觸發預先擷取的 Windows 市集應用程式在 Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)