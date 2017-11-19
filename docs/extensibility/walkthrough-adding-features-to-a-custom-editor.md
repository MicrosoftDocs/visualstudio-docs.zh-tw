---
title: "逐步解說： 加入功能與自訂編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df3621d87ae80c0eee105183edbc97a4e7ade62f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>逐步解說： 加入功能與自訂編輯器
建立自訂編輯器之後，您可以加入更多的功能。  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>若要建立 VSPackage 的編輯器  
  
1.  使用 Visual Studio Package 專案範本建立自訂編輯器。  
  
     如需詳細資訊，請參閱[逐步解說： 建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
2.  決定是否要讓您支援單一檢視或多個檢視的編輯器。  
  
     支援的編輯器**新視窗**命令，或有表單檢視和程式碼檢視中，需要個別的文件資料物件和文件檢視物件。 在支援單一檢視編輯器中，文件資料物件和文件檢視物件上實作相同的物件。  
  
     如需多個檢視的範例，請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
3.  編輯器 factory 實作藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  
  
     如需詳細資訊，請參閱[編輯器 Factory](../extensibility/editor-factories.md)。  
  
4.  決定您是否想要使用就地啟用編輯器，或簡化的嵌入管理文件檢視物件視窗。  
  
     簡化的嵌入編輯器視窗裝載標準文件檢視中時就地啟用編輯器視窗裝載 ActiveX 控制項或其他作用中的物件，當做其文件的檢視。 如需詳細資訊，請參閱[簡化內嵌](../extensibility/simplified-embedding.md)和[就地啟用](../extensibility/in-place-activation.md)。  
  
5.  實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面來處理命令。  
  
6.  提供文件的持續性和回應的外部檔案變更，執行下列動作：  
  
    1.  若要保留檔案，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>編輯器的文件資料物件上。  
  
    2.  若要回應外部檔案變更，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>編輯器的文件資料物件上。  
  
        > [!NOTE]
        >  呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>取得指標`IVsFileChangeEx`。  
  
7.  協調與原始程式碼控制的文件編輯事件。 做法：  
  
    1.  取得指標`IVsQueryEditQuerySave2`藉由呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>。  
  
    2.  第一次編輯事件發生時，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>方法。  
  
         這會提示使用者簽出檔案，如果它已不簽出。務必處理未簽出的 「 檔案 」 條件，以說明錯誤  
  
    3.  同樣地前, 儲存檔案，請先呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>方法。  
  
         這個方法會提示使用者儲存檔案，如果尚未儲存，或自上次儲存已變更。  
  
8.  啟用**屬性**視窗中顯示的文字編輯器 中選取的屬性。 做法：  
  
    1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>每次文字選取範圍變更時，傳遞的實作中<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  
  
    2.  呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服務取得的指標<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
9. 啟用使用者拖放項目之間的編輯器和**工具箱**，或外部編輯器 （例如 Microsoft Word) 之間和**工具箱**。 做法：  
  
    1.  實作`IDropTarget`您編輯器，可提醒 IDE，您的編輯器是在置放目標上。  
  
    2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>介面讓您的編輯器可以啟用和停用中的項目在檢視上**工具箱**。  
  
    3.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>服務取得的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>介面。  
  
         這可讓您的 VSPackage，加入新項目到**工具箱**。  
  
10. 決定您是否想其他選用的功能，編輯器。  
  
    -   如果您想要您的編輯器支援尋找和取代命令，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>。  
  
    -   如果您想要使用您在編輯器中的文件大綱工具視窗，實作`IVsDocOutlineProvider`。  
  
    -   如果您想要使用您在編輯器中的狀態列，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>呼叫`QueryService`如<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>取得指標`IVsStatusBar`。  
  
         比方說，編輯器可以顯示行 / 資料行資訊、 選取模式 （資料流 / 方塊），並插入模式 （插入 / 重疊印字）。  
  
    -   如果您想要您的編輯器支援`Undo`命令時，建議使用這個方法是使用 OLE 復原管理員模型。 或者，您可以將編輯器的控制代碼`Undo`直接命令。  
  
11. 建立登錄資訊，包括 Guid VSPackage、 功能表、 編輯器和其他功能。  
  
     以下是您會放置.rgs 檔案指令碼示範如何正確登錄編輯器中的程式碼的一般範例。  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. 實作即時線上說明支援。  
  
     這可讓您提供的編輯器中的項目支援的 F1 說明和動態說明 視窗。 如需詳細資訊，請參閱[How to： 將內容提供編輯器](../extensibility/how-to-provide-context-for-editors.md)。  
  
13. 藉由實作公開 Automation 物件模型，從您的編輯器`IDispatch`介面。  
  
     如需詳細資訊，請參閱[參與 Automation 模型](../extensibility/internals/contributing-to-the-automation-model.md)。  
  
## <a name="robust-programming"></a>穩固程式設計  
  
-   IDE 呼叫時，會建立編輯器執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。 如果編輯器支援多個檢視，`CreateEditorInstance`建立文件資料和文件檢視物件。 如果文件資料物件已經開啟，非 null`punkDocDataExisting`值會傳遞至`IVsEditorFactory::CreateEditorInstance`。 您的編輯器 factory 實作必須判斷現有文件資料物件是否相容，藉由查詢在其上的適當介面。 如需詳細資訊，請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
-   如果您使用簡單的內嵌方法，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面。  
  
-   如果您決定使用就地啟用，請實作下列介面：  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent`介面用來避免 OLE 2 功能表合併。  
  
     您`IOleCommandTarget`實作處理這類命令**剪下**，**複製**，和**貼上**。 當實作`IOleCommandTarget`，決定您的編輯器是否需要自己.vsct 檔案，以定義自己的命令功能表結構，或是如果它可以實作所定義的標準命令[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 通常，編輯器使用和擴充 IDE 的功能表，然後定義自己的工具列。 不過，通常就需要編輯器來定義自己的特定命令除了使用 IDE 的標準命令集。 若要這樣做，您的編輯器必須宣告的標準命令，它會使用，然後定義在.vsct 檔案中的 任何新的命令、 操作功能表中，最上層功能表和工具列。 如果您建立就地啟用編輯器，然後實作<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>並定義編輯器在.vsct 檔案而不是使用 OLE 2 功能表合併的功能表和工具列。  
  
-   若要避免過度擁擠 UI 中的功能表命令，您應該在 IDE 中使用現有的命令之前 ¬ 新命令。 SharedCmdDef.vsct 和 ShellCmdDef.vsct 中定義共用的命令。 這些檔案的 VisualStudioIntegration\Common\Inc 子目錄中的預設會安裝您[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]安裝。  
  
-   `ISelectionContainer`可以用來表示單一和多重選取項目。 每個選取的物件會實作為`IDispatch`物件。  
  
-   IDE 會實作`IOleUndoManager`以從可存取服務<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>或為物件，可以透過執行個體化<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>。 編輯器實作`IOleUndoUnit`每個介面`Undo`動作。  
  
-   有兩個地方的自訂編輯器可以公開 automation 物件：  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>另請參閱  
 [參與 Automation 模型](../extensibility/internals/contributing-to-the-automation-model.md)   
 [如何： 提供的內容編輯器](../extensibility/how-to-provide-context-for-editors.md)