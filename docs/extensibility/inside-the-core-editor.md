---
title: 核心編輯器內 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 243202b116af63a7d14672cd33d30030e8e987b0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959079"
---
# <a name="inside-the-core-editor"></a>在核心編輯器
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器是一份數個元件可讓您修改及查詢文字的資訊。 如果您已自訂核心編輯器使用舊版的 API，您可以繼續使用這些自訂項目，將會透過編輯器配接器進行路由。 不過，它會建議您調整您的自訂 API 的新編輯器。  
  
 下列區域為核心編輯器的一些重要特性：  
  
-   文字緩衝區  
  
-   文字檢視  
  
-   程式碼視窗  
  
-   文字標記  
  
-   文字管理員  
  
-   與語言服務整合  
  
## <a name="in-this-section"></a>本節內容  
 [使用舊版 API 具現化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 提供有關如何使用的逐步指示<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>編輯器建立核心的執行個體。  
  
 [使用舊版的 API 來存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 討論核心編輯器中的文字緩衝區的角色、 說明相關聯的系統，用來存取緩衝區，並提供一份文字緩衝區物件所實作的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 [在舊版的 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 提供一份用於文字緩衝區事件通知的介面。  
  
 [如何：註冊使用舊版 API 的文字緩衝區事件](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 描述如何通知文字緩衝區的事件。  
  
 [使用文字管理員監視全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 討論文字管理員用來與核心編輯器元件共用通用的喜好設定資訊的方式，以及如何接收通知的文字管理員事件。  
  
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 描述核心編輯器中的 [文字] 檢視的角色，並列出所實作的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
 [使用舊版 API 來自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 提供程式碼視窗如何用來括住文字檢視、 討論程式碼視窗管理員用來提供程式碼 視窗中，要裝飾的方式，並提供新檢視的通知的相關資訊。  
  
 [使用舊版的 API 來變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 提供有關如何強制檢視設定，以及如何移除強制的設定的逐步指示。  
  
 [語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md)  
 描述控制項的程式碼裝飾的語言服務的具現化。  
  
## <a name="related-sections"></a>相關章節  
 [逐步解說：建立核心編輯器 」 和 「 登錄編輯程式檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 提供有關如何啟動核心編輯器從 managed 程式碼的逐步指示。  
  
 [下拉式清單列](../extensibility/drop-down-bar.md)  
 討論如何在下拉式清單列會在程式碼視窗及說明您實作的下拉式清單列時所使用的介面。  
  
 [在舊版的 API 中使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)  
 說明文字標記，以及如何在核心編輯器中，使用它們的概念，並列出用來存取和管理文字標記的介面。  
  
 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)  
 提供有關如何建立文字標記以及如何將自訂命令新增至快顯功能表的逐步指示。  
  
 [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)  
 提供有關如何建立自訂文字標記，以及如何提供標記類型做為服務的逐步指示。