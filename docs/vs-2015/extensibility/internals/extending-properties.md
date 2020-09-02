---
title: 擴充屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690986"
---
# <a name="extending-properties"></a>擴充屬性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **屬性** ] 視窗是適用于 COM 和 com + 元件的通用屬性瀏覽器，並支援所有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 產品。 [ **屬性** ] 視窗適用于 `ITypeInfo` 型別資訊和 com + 中繼資料，可在整合式開發環境 (IDE) 的任何其他視窗中，列出目前所選物件的設計階段屬性。  
  
 [**屬性**] 視窗（可透過在鍵盤上按 F4 來開啟，或在 [**視圖**] 功能表上選取 [**屬性] 視窗**）是用來查看和編輯所選物件的與設定無關的設計階段屬性和事件。 與解決方案和專案相關聯的設定相依屬性會顯示在 [屬性頁](../../extensibility/internals/property-pages.md)上。 如需詳細資訊，請參閱 [ [筆尖：專案屬性](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)]、[ [管理設定選項](../../extensibility/internals/managing-configuration-options.md)] 和 [ [筆尖：專案中的專案管理](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)]。  
  
 ![屬性視窗概觀](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
屬性視窗  
  
 本節提供的詳細資訊與 [ **屬性** ] 視窗的個別區域，以及您必須執行並呼叫以填入視窗的介面相關。  
  
## <a name="in-this-section"></a>本節內容  
 [屬性視窗概觀](../../extensibility/internals/properties-window-overview.md)  
 說明 [ **屬性** ] 視窗相對於工具視窗和文件視窗的用途。  
  
 [範本原則和屬性視窗](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 討論如何將專案包含在企業範本專案中，以及該企業範本專案如何強制執行原則。  
  
 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 說明選取專案的基礎，以決定要在 [ **屬性** ] 視窗中顯示哪些資訊。  
  
 [屬性視窗的物件清單](../../extensibility/internals/properties-window-object-list.md)  
 描述 [ **屬性** ] 視窗物件清單的用途，描述如何，當這份清單中的不同物件觸發呼叫時，會通知環境已選取新的物件。  
  
 [屬性視窗的按鈕](../../extensibility/internals/properties-window-buttons.md)  
 說明 [ **屬性** ] 視窗工具列上顯示的四個預設按鈕的用途。  
  
 [屬性顯示格線](../../extensibility/internals/properties-display-grid.md)  
 說明在方格中找到屬性名稱和屬性值欄位的位置。  
  
 [宣告屬性視窗選取範圍追蹤](../../misc/announcing-property-window-selection-tracking.md)  
 描述 [ **屬性** ] 視窗的選取專案追蹤。  
  
 [隱藏具有子屬性的屬性](../../misc/hiding-properties-that-have-child-properties.md)  
 說明如何藉由執行介面，隱藏具有子屬性的屬性 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 。  
  
 [提供自訂屬性視窗](../../misc/providing-a-custom-properties-window.md)  
 詳細說明提供您自己的屬性瀏覽器的步驟。  
  
 [從屬性視窗中取得欄位描述](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 說明哪裡可以找到顯示所選屬性欄位相關資訊的 [描述] 區域。  
  
 [更新屬性視窗中的屬性值](../../misc/updating-property-values-in-the-properties-window.md)  
 提供逐步指示，說明將 [ **屬性** ] 視窗與屬性值變更同步處理的兩種方式。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論專案作為 IDE 的組建區塊 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)  
 描述 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 當您建立應用程式時，如何使用此平臺來持續測試和偵測應用程式。  
  
 [屬性視窗、HTML 文件屬性](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 提供直接從屬性視窗編輯 HTML 檔案的指示，並提供說明屬性視窗中的 HTML 檔案中欄位的表格。  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 描述 `IDispatch` 第一次設計來支援自動化的介面，提供晚期繫結機制來存取和取得物件之方法和屬性的相關資訊。  
  
 [筆尖：動態屬性簡介 (Visual Studio) ](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 提供動態屬性的總覽，讓您設定應用程式，讓屬性值儲存在外部設定檔中，而不是應用程式的已編譯器代碼。  
  
 [NIB︰以專案作為容器](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 將專案的角色描述為方案中的容器，以邏輯方式管理、建立和偵測構成應用程式的專案。  
  
 [筆尖：專案屬性](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 描述專案如何管理設定，這些設定可讓您控制套用至整個專案的屬性，以及限制為專案特定組建設定的屬性。  
  
 [方案和專案](../../ide/solutions-and-projects-in-visual-studio.md)  
 說明如何 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 有效率地管理透過方案和專案開發工作所需的專案，例如參考、資料連線、資料夾和檔案。  
  
 [擴充 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 服務建立 UI 項目，比對其餘的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。
