---
title: 使用舊版 API 將核心編輯器具現化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203915"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>使用舊版 API 將核心編輯器具現化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器負責文字編輯功能，例如插入、刪除、複製和貼上。 它會將這些函式與語言服務所提供的函式結合，例如文字著色、縮排和 IntelliSense 語句完成。  
  
 您可以使用下列三種方式之一來具現化核心編輯器的實例：  
  
- 在視窗中明確建立核心編輯器的實例。  
  
- 提供可傳回核心編輯器實例的編輯器 factory  
  
- 從專案階層開啟檔案。  
  
  下列各節將討論如何使用舊版 API 來具現化編輯器。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>明確開啟核心編輯器實例  
 明確取得核心編輯器的實例時：  
  
- 取得 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 以保存正在編輯的檔資料物件。  
  
- 藉由從介面建立介面，建立檔資料物件的線條導向標記法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>使用方法，設定為介面預設執行的實例的檔資料物件 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> 。  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>使用方法將實例裝載在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 介面中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> 。  
  
  此時，顯示 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 介面會提供一個視窗，內含核心編輯器的實例。  
  
  不過，這不是非常有用的實例，因為它沒有快速鍵或存取 advanced 功能。 取得快速鍵和 advanced 功能的存取權：  
  
- 您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 可以使用方法，將語言服務與編輯器所使用的檔資料物件產生關聯。  
  
- 您可以建立自己的快速鍵，或藉由設定物件顯示內容來使用系統預設值 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 。 若要這樣做，請 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> 使用屬性來呼叫方法 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 。  
  
   若要取得和使用非標準快速鍵，請使用 .vsct 檔案來產生它們。 如需詳細資訊，請參閱 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>如何使用編輯器 factory 取得核心編輯器  
 使用方法在編輯器 factory 中執行核心編輯器時 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ，請遵循上一節中所述的所有步驟， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 在物件中明確地使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 檔資料物件來裝載 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 。  
  
 若要顯示文字，請 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 從物件取得介面 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 方法。  
  
 若要為編輯器提供語言服務，請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 方法內的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。  
  
 若要取得預設快速鍵，與上一節不同，您可以在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 從方法取得核心編輯器時使用方法所傳回的命令內容 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。  
  
 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 方法傳回的命令 GUID 與文字編輯器相同，核心編輯器的實例就會自動取得預設快速鍵。  
  
 如需一般資訊，請參閱 [逐步解說：建立核心編輯器和註冊編輯器檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器中](../extensibility/inside-the-core-editor.md)   
 [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)   
 [逐步解說：建立核心編輯器和註冊編輯器檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
