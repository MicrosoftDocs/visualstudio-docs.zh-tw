---
title: 語言服務和核心編輯器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180296"
---
# <a name="language-services-and-the-core-editor"></a>語言服務及核心編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 中的編輯器經常與語言服務相關聯。 此外，語言服務會提供語法著色、語句完成、IntelliSense 和文字格式。  
  
## <a name="core-editors-and-document-data-objects"></a>核心編輯器和檔資料物件  
 當您存取核心編輯器時，不會建立檔資料和檔視圖物件。 IDE 會建立並控制這兩個物件，而您可以在編輯器 factory 的執行中進行適當的呼叫，以取得這些物件的控制碼。  
  
 如需詳細資訊，請參閱 [判斷哪個編輯器在專案中開啟](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)檔案。  
  
## <a name="language-services-and-the-core-editor"></a>語言服務及核心編輯器  
 藉由執行語言服務，您就可以控制資料在檔視圖中的顯示方式。 語言服務會提供特定語言的特定資訊和行為，例如 Visual C++。 當您建立文字緩衝區，並判斷要開啟之檔的副檔名時，文字緩衝區會從登錄機碼判斷與此副檔名相關聯的語言服務，HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions。 然後，標準 VSPackage 載入程式會載入您的 VSPackage，並建立您的語言服務實例。  
  
 基礎語言服務如下圖所示。  
  
 ![語言服務模型圖形](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
核心編輯器和語言服務物件  
  
 核心編輯器的檔資料物件稱為文字緩衝區，由 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件表示。 檔視圖物件稱為文字視圖，由 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 物件表示。 這兩個物件會透過語言服務共同運作，以提供核心編輯器的統一觀點。 文字緩衝區和文字視圖中的資訊會顯示在稱為程式碼視窗的文件視窗中。 程式碼視窗檔是由程式碼視窗管理員所管理。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [使用舊版 API 提供語言服務內容](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense 裝載](../extensibility/intellisense-hosting.md)   
 [包含的語言](../extensibility/contained-languages.md)   
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)
