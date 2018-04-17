---
title: 核心編輯器內 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e4612f5779d6177d58cef7f087ef6e11bbe4ebd9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-core-editor"></a>核心編輯器內
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器是一組可讓您修改和查詢文字資訊的數個元件。 如果您已自訂核心編輯器使用舊版的 API，您可以繼續使用這些自訂項目，將會路由到編輯器介面卡。 建議，不過，您調整您的自訂內容到新的編輯器應用程式開發介面。  
  
 下列各方面是核心編輯器的一些重要特性：  
  
-   文字緩衝區  
  
-   文字檢視  
  
-   程式碼視窗  
  
-   文字標記  
  
-   文字管理員  
  
-   與語言服務整合  
  
## <a name="in-this-section"></a>本節內容  
 [執行個體化使用舊版 API 的核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 提供有關如何使用的逐步指示<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>來建立執行個體的核心編輯器。  
  
 [使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 討論在核心編輯器中的文字緩衝區的角色、 說明用來存取緩衝區，並提供一份文字緩衝區物件所實作之介面的相關的系統<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 [在舊版 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 提供可用的文字緩衝區事件通知的介面清單。  
  
 [如何： 文字緩衝區使用註冊事件舊版應用程式開發介面](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 描述如何通知文字緩衝區的事件。  
  
 [使用文字管理員監控全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 討論如何將文字管理員用來與核心編輯器元件共用通用的喜好設定資訊和如何接收通知的文字管理員事件。  
  
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 描述核心編輯器中的 [文字] 檢視的角色，並列出所實作之介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
 [使用舊版 API 的自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 提供有關如何在程式碼視窗用來括住文字檢視，討論如何使用程式碼視窗管理員來提供程式碼 視窗中，裝飾並可提供新檢視的通知資訊。  
  
 [變更檢視設定，以使用舊版 API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 提供有關如何強制檢視設定及移除強制的設定的逐步指示。  
  
 [語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md)  
 描述控制項的程式碼裝飾的語言服務的具現化。  
  
## <a name="related-sections"></a>相關章節  
 [逐步解說： 建立核心編輯器和登錄編輯程式檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 提供有關如何啟動核心編輯器從 managed 程式碼的逐步指示。  
  
 [下拉式清單列](../extensibility/drop-down-bar.md)  
 討論如何使用程式碼視窗中的下拉式清單列，及說明實作下拉式清單列時所使用的介面。  
  
 [使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)  
 說明文字的標記，以及如何在核心編輯器中，使用它們的概念，並列出可用來存取和管理文字標記的介面。  
  
 [如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)  
 提供有關如何建立文字標記，以及如何將自訂命令新增至快顯功能表的逐步指示。  
  
 [如何： 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)  
 提供有關如何建立自訂文字標記，以及如何提供標記類型，以服務的逐步指示。