---
title: 擴充屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1a34edfbc6cede24f3238068549412d630827cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="extending-properties"></a>擴充屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **屬性**是 COM 和 COM + 元件的通用屬性瀏覽器視窗，並支援所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]產品。 **屬性**視窗搭配`ITypeInfo`類型資訊和 COM + 來列出目前選取的物件，在整合式的開發環境 (IDE) 中的任何其他視窗的設計階段屬性的中繼資料。  
  
 **屬性**視窗，可以藉由在鍵盤上，按 F4 或選取開啟**屬性] 視窗**上**檢視**功能表，用來檢視和編輯組態無關的設計階段屬性和事件的 [選取的物件。 方案和專案，與相關聯的組態相關屬性會顯示在[屬性頁](../../extensibility/internals/property-pages.md)。 如需詳細資訊，[管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
 ![屬性視窗概觀](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
屬性視窗  
  
 此章節提供詳細的資訊與相關的個別區域**屬性**視窗和您必須實作的介面來填入視窗呼叫。  
  
## <a name="in-this-section"></a>本節內容  
 [屬性視窗概觀](../../extensibility/internals/properties-window-overview.md)  
 說明的目的**屬性**相對於工具視窗與文件視窗的視窗。  
  
 [範本原則和屬性視窗](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 討論如何，專案包含在企業範本專案中，以及如何該企業樣板專案可以強制執行原則。  
  
 [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 說明可判斷哪些資訊會顯示在選取範圍的基礎**屬性**視窗。  
  
 [屬性視窗的物件清單](../../extensibility/internals/properties-window-object-list.md)  
 描述的目的**屬性**視窗物件清單中，描述如何，當不同的物件，此清單從觸發程序呼叫，環境會通知已選取新的物件。  
  
 [屬性視窗的按鈕](../../extensibility/internals/properties-window-buttons.md)  
 說明上顯示的四個預設按鈕的用途**屬性**視窗工具列。  
  
 [屬性顯示格線](../../extensibility/internals/properties-display-grid.md)  
 說明其中方格中找到的屬性名稱和屬性值欄位。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論專案做為建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)  
 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]進行持續測試及偵錯應用程式，當您建置的平台。  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 描述`IDispatch`介面，一開始是設計來支援自動化功能，提供晚期繫結機制，來存取和擷取資訊的方法和屬性的物件。  
  
 [管理應用程式設定 (.NET)](../../ide/managing-application-settings-dotnet.md)  
 提供可讓您設定您的應用程式，讓屬性值會儲存在外部組態檔，而不是應用程式的已編譯的程式碼的應用程式設定的概觀。  
  
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)  
 說明如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有效率地管理參考、 資料連接、 資料夾和檔案所需的開發工作透過方案和專案等項目。  
  
 [擴充 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]服務建立符合的其餘部分的 UI 項目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。