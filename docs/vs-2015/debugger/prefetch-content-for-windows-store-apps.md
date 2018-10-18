---
title: 預先擷取 Windows 市集應用程式的內容 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9329cad2f0125288aeea146070188d023d1a126
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211441"
---
# <a name="prefetch-content-for-windows-store-apps"></a>預先擷取 Windows 市集應用程式的內容
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

僅適用於 Windows] (../Image/windows_only_content.png"windows_only_content")  
  
 若要讓 Windows 市集應用程式回應速度更快，您可以要求預先部分網頁內容，例如網頁或影像載入至應用程式的 Windows [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)快取。 這項功能稱為預先擷取。 如果是啟動時會用到的內容，這種方式就特別有效。但是，您也可以預先擷取其他經常用到的內容。 方法[Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx)類別可讓您指定您想要預先載入內容 Uri。 請參閱 Windows SDK[內容預先擷取範例](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)如需如何將 ContentPrefetcher 功能加入至您的應用程式的範例。  
  
 Windows 會使用啟發學習法，判斷預先擷取的發生時機、是否要預先擷取以及要下載的資源。 啟發學習法會將系統網路和電源狀況、使用者應用程式使用歷程記錄，以及先前嘗試預先擷取的結果都納入考量。 在 Visual Studio 中，您可以使用**觸發 Windows 市集應用程式預先擷取**命令強制 Windows 忽略 ContentPrefetcher 啟發學習法並預先載入所有指定的 web 內容。 如果您要測試應用程式的行為或效能，並且要在已知的狀態 (已載入或未載入) 下預先擷取內容，這個命令就很有用。  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>若要強制 ContentPrefetcher 預先載入指定的資源  
 下列程序會假設您已經設定 ContentPrefetcher 功能，而且已指定要在應用程式專案中預先載入的內容 URI。 若要新增或修改指定的資源時，請強制預先載入內容，您必須先啟動，然後停止應用程式，再選擇**觸發 Windows 市集應用程式預先擷取**命令。 您要先執行應用程式以註冊 URI。 **觸發 Windows 市集應用程式預先擷取**命令會強制 ContentPrefetcher 下載內容，並將它加入快取。 未來執行應用程式時，您就可以認定內容已經預先載入。  
  
1.  啟動應用程式，向應用程式註冊預先擷取內容 URI。 在 **偵錯**功能表上，選擇**開始偵錯**(鍵盤快速鍵： F5)。  
  
2.  在 **偵錯**功能表上，選擇**停止偵錯**(鍵盤快速鍵： Shift + F5)。  
  
3.  在 **偵錯**功能表上，選擇**其他偵錯目標**，然後選擇**觸發 Windows 市集應用程式預先擷取**。  
  
 現在您可以在已經預先擷取 Web 資源的情況下偵錯、測試或分析應用程式。  
  
> [!NOTE]
>  當您新增或修改指定的 Web 內容時，請重複上述步驟。  
  
## <a name="see-also"></a>另請參閱  
 [部落格文章： 觸發預先擷取適用於 Windows 市集應用程式在 Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)



