---
title: 逐步解說：將功能加入至自訂編輯器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fa926b21171c3e09b5a0f4d74e9415da090bf2f
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2019
ms.locfileid: "73569068"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>逐步解說：將功能加入至自訂編輯器
建立自訂編輯器之後，您可以在其中新增更多功能。

## <a name="to-create-an-editor-for-a-vspackage"></a>若要建立 VSPackage 的編輯器

1. 使用 [Visual Studio 封裝] 專案範本建立自訂編輯器。

     如需詳細資訊，請參閱[逐步解說：建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。

2. 決定您是否要讓編輯器支援單一或多個視圖。

     支援**新的視窗**命令，或具有表單檢視和程式碼視圖的編輯器，需要個別的檔資料物件和檔視圖物件。 在只支援單一視圖的編輯器中，可以在相同的物件上執行檔資料物件和檔視圖物件。

     如需多個視圖的範例，請參閱[支援多個檔視圖](../extensibility/supporting-multiple-document-views.md)。

3. 藉由設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 介面來執行編輯器 factory。

     如需詳細資訊，請參閱[編輯器工廠](../extensibility/editor-factories.md)。

4. 決定您是否要讓編輯器使用就地啟用或簡化內嵌來管理 [檔視圖] 物件視窗。

     簡化的內嵌編輯器視窗會裝載標準檔視圖，而就地啟用編輯器視窗則裝載 ActiveX 控制項或其他作用中物件做為其檔視圖。 如需詳細資訊，請參閱[簡化](../extensibility/simplified-embedding.md)的內嵌和[就地啟用](/visualstudio/misc/in-place-activation?view=vs-2015)。

5. 執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來處理命令。

6. 提供檔持續性和對外部檔案變更的回應：

    1. 若要保存檔案，請在您的編輯器檔資料物件上執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>。

    2. 若要回應外部檔案變更，請在您的編輯器檔資料物件上執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>。

        > [!NOTE]
        > 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> 上的 `QueryService`，以取得 `IVsFileChangeEx`的指標。

7. 使用原始程式碼控制協調檔編輯事件。 請依照下列步驟：

    1. 藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>上的 `QueryService`，取得 `IVsQueryEditQuerySave2` 的指標。

    2. 發生第一個編輯事件時，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法。

         如果檔案尚未簽出，這個方法會提示使用者簽出該檔案。請務必處理「檔案未簽出」條件，以避免發生錯誤。

    3. 同樣地，在儲存檔案之前，請先呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 方法。

         這個方法會提示使用者儲存檔案（如果尚未儲存），或是自從上次儲存後是否有變更。

8. 啟用 [**屬性**] 視窗，以顯示在編輯器中選取之文字的屬性。 請依照下列步驟：

    1. 在每次文字選取變更時呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>，傳入您的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>的執行。

    2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 服務上的 `QueryService`，以取得 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>的指標。

9. 讓使用者可以在編輯器和**工具箱**之間，或在外部編輯器（例如 Microsoft Word）和 [**工具箱**] 之間拖放專案。 請依照下列步驟：

    1. 在您的編輯器上執行 `IDropTarget`，以在 IDE 中警示您的編輯器是放置目標。

    2. 在視圖上執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 介面，讓您的編輯器可以在 [**工具箱**] 中啟用和停用專案。

    3. 在 <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 服務上執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> 並呼叫 `QueryService`，以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 介面的指標。

         這些步驟可讓您的 VSPackage 將新專案新增至 [**工具箱**]。

10. 決定您是否想要編輯器的其他選用功能。

    - 如果您想要編輯器支援 [尋找和取代] 命令，請執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>。

    - 如果您想要在編輯器中使用 [檔大綱] 工具視窗，請執行 `IVsDocOutlineProvider`。

    - 如果您想要在編輯器中使用狀態列，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 並呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 的 `QueryService`，以取得 `IVsStatusBar`的指標。

         例如，編輯器可以顯示行/欄資訊、選取模式（資料流程/方塊）和插入模式（插入/覆寫）。

    - 如果您想要編輯器支援 `Undo` 命令，建議的方法是使用 OLE 復原管理員模型。 或者，您可以讓編輯器直接處理 `Undo` 命令。

11. 建立登錄資訊，包括 VSPackage、功能表、編輯器和其他功能的 Guid。

     以下是您要放入 *.rgs*檔案腳本中的一般程式碼範例，以示範如何正確地註冊編輯器。

    ```csharp
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

12. 執行上下文相關的説明支援。

     此步驟可讓您在編輯器中提供專案的 F1 說明和動態說明視窗支援。 如需詳細資訊，請參閱[如何：提供編輯器的內容](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015)。

13. 藉由執行 `IDispatch` 介面，從您的編輯器公開 Automation 物件模型。

     如需詳細資訊，請參閱 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)。

## <a name="robust-programming"></a>穩固程式設計

- 當 IDE 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 方法時，就會建立編輯器實例。 如果編輯器支援多個視圖，`CreateEditorInstance` 會同時建立檔資料和檔視圖物件。 如果檔資料物件已開啟，則會將非 null 的 `punkDocDataExisting` 值傳遞給 `IVsEditorFactory::CreateEditorInstance`。 您的編輯器 factory 必須藉由查詢其上的適當介面，判斷現有的檔資料物件是否相容。 如需詳細資訊，請參閱[支援多個檔視圖](../extensibility/supporting-multiple-document-views.md)。

- 如果您使用簡化的內嵌方法，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面。

- 如果您決定使用就地啟用，請執行下列介面：

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > `IOleInPlaceComponent` 介面是用來避免 OLE 2 功能表合併。

   您的 `IOleCommandTarget` 執行會處理命令，例如**剪**下、**複製**和**貼**上。 在執行 `IOleCommandTarget`時，請決定您的編輯器是否需要自己的 *.vsct*檔案來定義自己的命令功能表結構，或是否可以執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]所定義的標準命令。 通常，編輯器會使用並擴充 IDE 的功能表，並定義自己的工具列。 不過，除了使用 IDE 的標準命令集之外，編輯器通常還需要定義自己的特定命令。 您的編輯器必須宣告所使用的標準命令，然後在 *.vsct*檔案中定義任何新的命令、內容功能表、最上層功能表和工具列。 如果您建立就地啟用編輯器，請在 *.vsct*檔案中執行 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> 並定義編輯器的功能表和工具列，而不是使用 OLE 2 功能表合併。

- 若要防止 UI 中的功能表命令根本，您應該在發明新命令之前，先使用 IDE 中的現有命令。 共用命令定義于*SharedCmdDef. .vsct*和*ShellCmdDef. .vsct*中。 這些檔案預設會安裝在 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 安裝的 VisualStudioIntegration\Common\Inc 子目錄中。

- `ISelectionContainer` 可以同時表示單一和多重選取專案。 每個選取的物件都會實作為 `IDispatch` 物件。

- IDE 會將 `IOleUndoManager` 做為可從 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 存取的服務，或當做可以透過 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>具現化的物件。 您的編輯器會針對每個 `Undo` 動作執行 `IOleUndoUnit` 介面。

- 有兩個地方，自訂編輯器可以公開 automation 物件：

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>請參閱

- [參與 automation 模型](../extensibility/internals/contributing-to-the-automation-model.md)