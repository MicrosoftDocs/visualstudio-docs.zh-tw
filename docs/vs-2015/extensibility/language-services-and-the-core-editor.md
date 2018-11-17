---
title: 語言服務及核心編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 503924f435dda2d4432c915f9566846f0f4dd964
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727307"
---
# <a name="language-services-and-the-core-editor"></a>語言服務及核心編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中的編輯器的常見問題與服務相關聯的語言。 除此之外，語言服務會提供語法著色、 陳述式完成、 IntelliSense 和文字格式設定。  
  
## <a name="core-editors-and-document-data-objects"></a>核心編輯器和文件資料物件  
 當您存取核心編輯器時，您不要建立文件資料和文件檢視物件。 IDE 會建立並控制這兩個物件，並進行適當的呼叫，在您的編輯器 factory 實作取得它們的控制代碼。  
  
 如需詳細資訊，請參閱 <<c0> [ 判斷哪一個編輯器在專案中開啟檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="language-services-and-the-core-editor"></a>語言服務及核心編輯器  
 藉由實作語言服務，您可以控制文件檢視中顯示資料的方式。 語言服務會提供資訊和給定的語言，例如 Visual c + + 特有的行為。 當您建立的文字緩衝區，並判斷您要開啟的文件的副檔名時，文字緩衝區判斷要從登錄機碼，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors 檔案副檔名相關聯的語言服務\\{YourLanguageService GUID} \Extensions。 標準的 VSPackage，載入程序，然後載入 VSPackage，並建立您的語言服務的執行個體。  
  
 基本語言服務是由下列圖所示。  
  
 ![語言服務模型圖形](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
核心編輯器和語言服務的物件  
  
 核心編輯器的文件資料物件會呼叫文字緩衝區，而且會以表示<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件。 文件檢視物件稱為文字檢視，而由<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>物件。 透過提供統一的核心編輯器檢視語言服務，這兩個物件一起運作。 從文字緩衝區和文件視窗中的文字 檢視會顯示的資訊稱為 「 程式碼視窗。 程式碼視窗的文件是由程式碼視窗管理員管理。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [使用舊版 API 提供的語言服務內容](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense 裝載](../extensibility/intellisense-hosting.md)   
 [包含的語言](../extensibility/contained-languages.md)   
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)

