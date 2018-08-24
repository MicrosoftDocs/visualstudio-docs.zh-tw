---
title: 擴充屬性 |Microsoft Docs
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
ms.openlocfilehash: 77b5861dd084098e561f3642b5738dd0279d4b52
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512105"
---
# <a name="extend-properties"></a>擴充屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **屬性** 視窗是 COM 和 COM + 元件的通用屬性瀏覽器，並支援所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]產品。 **屬性** 視窗的運作方式與`ITypeInfo`類型資訊和 COM + 來列出目前選取的物件，在整合式的開發環境 (IDE) 中的任何其他視窗的設計階段屬性的中繼資料。  
  
 **屬性**視窗中，按下可開啟**F4**在鍵盤上，或選取**屬性 視窗**上**檢視** 功能表中，用來檢視和編輯所選物件的設定無關的設計階段屬性和事件。 方案和專案，與相關聯的組態相關屬性會顯示在[屬性頁](../../extensibility/internals/property-pages.md)。 如需詳細資訊，[管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
 ![屬性視窗概觀](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
屬性視窗  
  
 本節提供相關的個別區域的詳細的資訊**屬性**視窗，您必須實作的介面和填入視窗呼叫。  
  
## <a name="in-this-section"></a>本節內容  
 [屬性視窗概觀](../../extensibility/internals/properties-window-overview.md)  
 說明的目的**屬性**相對於工具視窗和文件視窗的視窗。  
  
 [範本原則和 [屬性] 視窗](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 討論如何，專案包含在 enterprise 範本專案中，以及如何該企業樣板專案可以強制執行原則。  
  
 [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 說明可決定哪些資訊會顯示在選取範圍的基礎**屬性**視窗。  
  
 [屬性視窗的物件清單](../../extensibility/internals/properties-window-object-list.md)  
 描述的用途**屬性**視窗的物件清單，描述如何進行，請從這份清單的不同物件觸發時呼叫，環境會通知已選取新的物件。  
  
 [屬性視窗的按鈕](../../extensibility/internals/properties-window-buttons.md)  
 說明上顯示的四個預設按鈕的用途**屬性**視窗工具列。  
  
 [屬性顯示格線](../../extensibility/internals/properties-display-grid.md)  
 說明，在方格中找到的屬性名稱和屬性值欄位。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論專案做為建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)  
 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]持續測試及偵錯應用程式，當您建立它們的平台。  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 描述`IDispatch`介面，首先應支援 automation、 提供晚期繫結機制，來存取並擷取資訊的方法和屬性的物件。  
  
 [管理應用程式設定 (.NET)](../../ide/managing-application-settings-dotnet.md)  
 提供可讓您設定您的應用程式，使屬性值會儲存在外部組態檔而不是應用程式的已編譯的程式碼的應用程式設定的概觀。  
  
 [方案和專案](../../ide/solutions-and-projects-in-visual-studio.md)  
 說明如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有效率地管理參考、 資料連接、 資料夾和您透過方案和專案的開發工作所需的檔案等項目。  
  
 [擴充 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]服務，以建立比對的其餘的 UI 項目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。