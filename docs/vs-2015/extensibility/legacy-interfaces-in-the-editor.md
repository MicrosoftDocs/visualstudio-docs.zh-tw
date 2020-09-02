---
title: 編輯器中的舊版介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180283"
---
# <a name="legacy-interfaces-in-the-editor"></a>編輯器中的舊版介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以從舊版介面存取 Visual Studio 編輯器。 Visual Studio SDK 包含稱為 *填充*碼的介面卡，可讓這些介面與新的編輯器互動。 不過，我們建議您更新舊版程式碼，以使用新的編輯器 API。 您的程式碼會執行得更好，而且您可以使用新的技術，例如 Windows Presentation Foundation (WPF) 和 Managed Extensibility Framework (MEF) 。  
  
## <a name="related-topics"></a>[相關主題]  
  
|標題|描述|  
|-----------|-----------------|  
|[使舊版程式碼配合編輯器](../extensibility/adapting-legacy-code-to-the-editor.md)|說明如何將您的程式碼調整為新的編輯器。|  
|[編輯器配接器的新行為或變更行為](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|說明編輯器介面卡的行為與舊版編輯器的行為有何不同。|  
|[深入探索核心編輯器](../extensibility/inside-the-core-editor.md)|描述舊版編輯器的不同元件。|  
|[使用舊版 API 將核心編輯器具現化](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|說明如何使用舊版 API 將核心編輯器具現化。|  
|[編輯器處理站](../extensibility/editor-factories.md)|說明如何搭配舊版 API 使用編輯器 factory。|  
|[如何：註冊編輯器檔案類型](../extensibility/how-to-register-editor-file-types.md)|說明如何將副檔名連結至編輯器。|  
|[逐步解說：建立核心編輯器和註冊編輯器檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|說明如何建立核心編輯器，並連結其副檔名。|  
|[如何：為編輯器提供內容](../extensibility/how-to-provide-context-for-editors.md)|說明如何為編輯器提供內容。|  
|[語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md)|說明語言服務與編輯器之間的互動。|  
|[使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|說明如何使用舊版 API 存取文字緩衝區。|  
|[使用舊版 API 存取文字檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|說明如何使用舊版 API 存取文字視圖。|  
|[使用舊版 API 自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|說明如何使用舊版 API 自訂程式碼視窗。|  
|[使用舊版 API 存取文字層](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|說明如何使用舊版 API 來存取不同的文字層。|  
|[以舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)|說明如何使用舊版 API 來新增文字標記。|  
|[使用舊版 API 自訂編輯器控制項及功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|說明如何使用舊版 API 自訂編輯器控制項。|  
|[使用舊版 API 管理復原和重做](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|說明如何使用舊版 API 來管理復原和重做。|  
|[如何：實作尋找和取代機制](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|說明如何使用舊版 API 來管理尋找和取代。|  
|[如何：隱藏檔案變更通知](../extensibility/how-to-suppress-file-change-notifications.md)|說明如何使用舊版 API 來抑制檔案變更通知。|  
|[建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)|說明如何建立自訂編輯器和設計工具。|  
|[開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)|提供功能的相關檔連結，這些功能可透過新增語言服務的支援，提供自訂功能給 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 核心編輯器。|  
|[使用字型和色彩](../extensibility/using-fonts-and-colors.md)|說明如何搭配舊版介面使用字型和色彩。|
