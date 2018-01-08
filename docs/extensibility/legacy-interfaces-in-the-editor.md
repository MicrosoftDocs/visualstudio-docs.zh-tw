---
title: "在編輯器中的傳統介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a9d09c452fb6d03f7f5072e34813c3757455f96a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-interfaces-in-the-editor"></a>在編輯器中的傳統介面
您可以從舊版的介面存取 Visual Studio 編輯器。 Visual Studio SDK 包括配接器稱為*填充碼*，可讓這些介面，以新的編輯器進行互動。 不過，我們建議您更新您要使用新的編輯器 API 的舊版程式碼。 您的程式碼執行效能，您可以使用新的技術，例如 Windows Presentation Foundation (WPF) 和 Managed Extensibility Framework (MEF)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[改寫舊版程式碼編輯器](../extensibility/adapting-legacy-code-to-the-editor.md)|說明如何調整到新的編輯器程式碼。|  
|[新增或變更的行為，與編輯器介面卡](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|說明從舊版的編輯器 中的編輯器配接器的行為差異。|  
|[核心編輯器內](../extensibility/inside-the-core-editor.md)|描述舊版的編輯器 中的不同元件。|  
|[執行個體化使用舊版 API 的核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|說明如何使用舊版的 API 來具現化核心編輯器。|  
|[編輯器 Factory](../extensibility/editor-factories.md)|說明如何搭配舊版的應用程式開發介面使用編輯器 factory。|  
|[如何： 註冊編輯器檔案類型](../extensibility/how-to-register-editor-file-types.md)|說明如何將檔案的副檔名連結至您的編輯器。|  
|[逐步解說： 建立核心編輯器和登錄編輯程式檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|說明如何建立核心編輯器和連結此檔案的副檔名。|  
|[如何： 提供的內容編輯器](../extensibility/how-to-provide-context-for-editors.md)|說明如何為您的編輯器提供內容。|  
|[語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md)|說明語言服務與編輯器之間的互動。|  
|[使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|說明如何使用舊版 API 存取文字緩衝區。|  
|[使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|說明如何使用舊版的 API 來存取 [文字] 檢視。|  
|[使用舊版 API 的自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|說明如何使用舊版 API 自訂程式碼視窗。|  
|[使用舊版 API 存取文字圖層](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|說明如何使用舊版 API 存取不同的圖層的文字。|  
|[使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)|說明如何使用舊版 API 新增文字標記。|  
|[使用舊版 API 自訂編輯器控制項和功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|說明如何使用舊版 API 自訂編輯器控制項。|  
|[管理復原和取消復原使用舊版 API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|說明如何管理復原和取消復原使用舊版 API。|  
|[如何： 實作 尋找和取代機制](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|說明如何管理 尋找和取代使用舊版 API。|  
|[如何： 隱藏檔案變更告知](../extensibility/how-to-suppress-file-change-notifications.md)|說明如何使用舊版 API 隱藏檔案變更告知。|  
|[建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)|說明如何建立自訂編輯器和設計工具。|  
|[開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)|提供功能，可提供自訂功能的相關文件的連結[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器，藉由新增語言服務的支援。|  
|[使用字型和色彩](../extensibility/using-fonts-and-colors.md)|說明如何搭配舊版的介面中使用的字型和色彩。|