---
title: "執行個體化使用舊版 API 的核心編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a82f420203b88bb94531401d061493621f3eba93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>執行個體化使用舊版 API 的核心編輯器
編輯器會負責文字編輯功能，例如插入、 刪除、 複製和貼。 它會結合這些函式提供的語言服務，例如文字著色、 縮排和 IntelliSense 陳述式完成。  
  
 您可以具現化執行個體的核心編輯器，在三種方式之一：  
  
-   明確建立執行的個體的核心編輯器視窗中。  
  
-   提供編輯器處理站會傳回核心編輯器的執行個體  
  
-   從專案階層架構中開啟檔案。  
  
 下列各節討論如何使用舊版的 API 來具現化的編輯器。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>明確開啟核心編輯器執行個體  
 當明確取得核心編輯器的執行個體：  
  
-   取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>來保存要編輯的文件資料物件。  
  
-   建立文件資料物件導向的線條表示法建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面。  
  
-   設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>做為文件資料物件的預設實作的執行個體<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>介面、 使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>方法。  
  
     主機<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>執行個體中<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>方法。  
  
 此時，顯示<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面提供視窗，其中包含核心編輯器的執行個體。  
  
 不過，這不是非常有用的執行個體，因為它沒有快速鍵，或存取進階功能。 若要取得存取攠摝坫和進階的功能：  
  
-   使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>語言服務及編輯器使用的文件資料物件之間建立關聯的方法。  
  
-   建立您自己的快速鍵，或使用系統預設值，藉由設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>物件不會顯示屬性。 若要這樣做，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>屬性。  
  
     若要取得並使用非標準的快速鍵，產生使用.vsct 檔案。 如需詳細資訊，請參閱 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>如何使用編輯器 factory 取得核心編輯器  
 當實作編輯器處理站使用的核心編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，遵循所有步驟，以明確裝載上一節中所述<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>文件資料物件，在<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>物件。  
  
 若要將文字顯示，取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>物件並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  
  
 若要提供語言服務給編輯器時，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法內<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  
  
 若要取得預設快速鍵，不同於上一節中，您會使用所傳回的命令內容<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法取得從核心編輯器時<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  
  
 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法會傳回做為文字編輯器在同一個命令的 GUID，執行個體的核心編輯器中自動取得預設快速鍵。  
  
 如需一般資訊，請參閱[逐步解說： 建立核心編輯器和註冊編輯器檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [逐步解說： 建立核心編輯器和登錄編輯程式檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)