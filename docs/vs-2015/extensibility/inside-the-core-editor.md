---
title: 在核心編輯器中 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203958"
---
# <a name="inside-the-core-editor"></a>深入探索核心編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]核心編輯器是數個元件的集合，可讓您修改和查詢文字資訊。 如果您已使用舊版 API 自訂核心編輯器，您可能會繼續使用這些自訂，這些自訂會透過編輯器介面卡進行路由。 不過，建議您將自訂調整為新的編輯器 API。  
  
 下欄區域是核心編輯器的一些重要層面：  
  
- 文字緩衝區  
  
- 文字視圖  
  
- 程式碼視窗  
  
- 文字標記  
  
- 文字管理員  
  
- 與語言服務整合  
  
## <a name="in-this-section"></a>本節內容  
 [使用舊版 API 將核心編輯器具現化](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 提供有關如何使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 建立核心編輯器實例的逐步指示。  
  
 [使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 討論核心編輯器中的文字緩衝區角色、說明用來存取緩衝區的相關聯繫統，並提供文字緩衝區物件所執行的介面清單 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 。  
  
 [舊版 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 提供用來通知文字緩衝區事件的介面清單。  
  
 [如何：使用舊版 API 註冊文字緩衝區事件](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 描述如何建議文字緩衝區事件。  
  
 [使用文字管理員監視全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 討論如何使用文字管理員與核心編輯器元件共用全域喜好設定資訊，以及如何接收文字管理員事件的通知。  
  
 [使用舊版 API 存取文字檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 描述「核心編輯器」中的文字視圖的角色，並列出物件所執行的介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 。  
  
 [使用舊版 API 自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 提供有關如何使用程式碼視窗來括住文字視圖的資訊，討論如何使用程式碼視窗管理員為程式碼視窗提供裝飾，以及提供新視圖的通知。  
  
 [使用舊版 API 變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 提供逐步指示，說明如何強制進行視圖設定，以及如何移除強制設定。  
  
 [語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md)  
 描述語言服務的具現化以控制程式代碼裝飾。  
  
## <a name="related-sections"></a>相關章節  
 [逐步解說：建立核心編輯器和註冊編輯器檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 提供逐步指示，說明如何從 managed 程式碼啟動核心編輯器。  
  
 [下拉式功能表列](../extensibility/drop-down-bar.md)  
 討論如何在程式碼視窗中使用下拉式清單，並描述您在執行下拉式列時所使用的介面。  
  
 [以舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)  
 解說文字標記的概念，以及它們在核心編輯器中的使用方式，並列出用來存取和管理文字標記的介面。  
  
 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)  
 提供逐步指示，說明如何建立文字標記，以及如何將自訂命令新增至快捷方式功能表。  
  
 [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)  
 提供逐步指示，說明如何建立自訂文字標記，以及如何將標記類型提供為服務。
