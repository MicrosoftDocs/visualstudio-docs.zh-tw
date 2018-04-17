---
title: 語言服務及核心編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c3d2bcad21bb919125b487a57b73d3a458a3a1f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="language-services-and-the-core-editor"></a>語言服務及核心編輯器
在 Visual Studio 中的編輯器的常見問題與服務相關聯的語言。 在其他方面，語言服務會提供語法著色、 陳述式完成、 IntelliSense 和文字格式設定。  
  
## <a name="core-editors-and-document-data-objects"></a>核心編輯器和文件資料物件  
 當您存取核心編輯器時，您不要建立文件資料和文件檢視物件。 IDE 會建立並控制這兩個物件，而且藉由適當地呼叫編輯器 factory 實作會取得它們的控制代碼。  
  
 如需詳細資訊，請參閱[判斷哪一個編輯器在專案中開啟檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="language-services-and-the-core-editor"></a>語言服務及核心編輯器  
 藉由實作語言服務，您可以控制資料中的文件檢視的顯示方式。 語言服務會提供資訊和指定的語言，例如 Visual c + + 特定的行為。 當您建立文字緩衝區，並判斷您所開啟的文件檔名的副檔名時，文字緩衝區會判斷登錄機碼，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors 檔案副檔名相關聯的語言服務\\{YourLanguageService GUID} \Extensions。 標準的 VSPackage，載入程序，然後載入 VSPackage，並建立您的語言服務執行個體。  
  
 在下圖顯示基本語言服務。  
  
 ![語言服務模型圖形](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
核心編輯器和語言服務的物件  
  
 核心編輯器文件資料物件稱為文字緩衝區，而由<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件。 文件檢視物件稱為文字檢視，而由<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>物件。 透過提供統一的核心編輯器檢視，語言服務，這兩個物件一起運作。 從文字緩衝區和文件視窗中的文字 檢視會顯示的資訊呼叫程式碼視窗。 程式碼視窗的文件是由程式碼視窗管理員管理。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [語言服務內容，使用提供的舊版應用程式開發介面](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense 裝載](../extensibility/intellisense-hosting.md)   
 [所包含的語言](../extensibility/contained-languages.md)   
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)