---
title: 逐步解說：將功能新增至自訂編輯器 |Microsoft Docs
description: 瞭解如何在使用本逐步解說建立編輯器之後，將其他功能加入至自訂編輯器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c08af63eaf68701f1a6703ac41fec20368d78931
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863195"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>逐步解說：將功能新增至自訂編輯器
建立自訂編輯器之後，您可以在其中加入更多功能。

## <a name="to-create-an-editor-for-a-vspackage"></a>若要建立 VSPackage 的編輯器

1. 使用 Visual Studio 套件專案範本建立自訂編輯器。

     如需詳細資訊，請參閱 [逐步解說：建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。

2. 決定您是否要讓編輯器支援單一視圖或多個視圖。

     支援 **新視窗** 命令或具有表單檢視和程式碼視圖的編輯器，需要個別的檔資料物件和檔視圖物件。 在只支援單一視圖的編輯器中，可以在相同的物件上執行檔資料物件和檔視圖物件。

     如需多個視圖的範例，請參閱 [支援多個檔的視圖](../extensibility/supporting-multiple-document-views.md)。

3. 藉由設定介面來執行編輯器 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 。

     如需詳細資訊，請參閱 [編輯器](/previous-versions/visualstudio/visual-studio-2015/extensibility/editor-factories?preserve-view=true&view=vs-2015)factory。

4. 決定您是否想要編輯器使用就地啟用或簡化內嵌來管理檔視圖物件視窗。

     簡化的內嵌編輯器視窗會主控標準檔視圖，而就地啟用編輯器視窗則會裝載 ActiveX 控制項或其他使用中的物件做為其檔視圖。 如需詳細資訊，請參閱 [簡化](../extensibility/simplified-embedding.md) 內嵌和就地 [啟用](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015)。

5. 執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來處理命令。

6. 針對外部檔案變更提供檔持續性和回應：

    1. 若要保存檔案， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 請 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 在編輯器的檔資料物件上執行和。

    2. 若要回應外部檔案變更，請 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 在編輯器的檔資料物件上執行和。

        > [!NOTE]
        > 呼叫 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> 以取得的指標 `IVsFileChangeEx` 。

7. 使用原始程式碼控制協調檔編輯事件。 依照下列步驟執行：

    1. 藉由呼叫來取得的指標 `IVsQueryEditQuerySave2` `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 。

    2. 當第一個編輯事件發生時，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法。

         如果檔案尚未簽出，則此方法會提示使用者簽出檔案。請務必處理「檔案未簽出」條件，以避免發生錯誤。

    3. 同樣地，在儲存檔案之前，請先呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 方法。

         如果檔案尚未儲存或自上次儲存後已變更，則此方法會提示使用者儲存檔案。

8. 啟用 [ **屬性** ] 視窗，即可顯示在編輯器中選取之文字的屬性。 依照下列步驟執行：

    1. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>每次文字選取變更時呼叫，並傳入您的實作為 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 。

    2. 呼叫 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 服務以取得的指標 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 。

9. 讓使用者在編輯器和 **工具箱** 之間，或在外部編輯器 (（例如 Microsoft Word) 和 **工具箱**）之間，拖放專案。 依照下列步驟執行：

    1. `IDropTarget`在編輯器上執行，以警示 IDE 編輯器是放置目標。

    2. 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 視圖上執行介面，讓您的編輯器可以在 [ **工具箱**] 中啟用和停用專案。

    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>在服務上執行和呼叫， `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 。

         這些步驟可讓您的 VSPackage 將新專案新增至 [ **工具箱**]。

10. 決定您是否想要編輯器的任何其他選用功能。

    - 如果您想要編輯器支援尋找和取代命令，請執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> 。

    - 如果您想要在編輯器中使用 [檔大綱] 工具視窗，請執行 `IVsDocOutlineProvider` 。

    - 如果您想要在編輯器中使用狀態列，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 並呼叫， `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 以取得的指標 `IVsStatusBar` 。

         例如，編輯器可以顯示行/欄資訊、選取模式 (stream/box) ，以及 (insert/覆寫) 插入模式。

    - 如果您希望編輯器支援 `Undo` 命令，建議的方法是使用 OLE 復原管理員模型。 或者，您可以讓編輯器 `Undo` 直接處理命令。

11. 建立登錄資訊，包括 VSPackage、功能表、編輯器和其他功能的 Guid。

     以下是程式碼的一般範例，您會將它放在 *.rgs* 檔腳本中，以示範如何正確地註冊編輯器。

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

12. 執行即時線上說明支援。

     此步驟可讓您為編輯器中的專案提供 F1 說明和動態說明視窗支援。 如需詳細資訊，請參閱 [如何：提供編輯器的內容](/previous-versions/visualstudio/visual-studio-2015/extensibility/how-to-provide-context-for-editors?preserve-view=true&view=vs-2015)。

13. 藉由執行介面，從編輯器公開 Automation 物件模型 `IDispatch` 。

     如需詳細資訊，請參閱 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)。

## <a name="robust-programming"></a>穩固程式設計

- 當 IDE 呼叫方法時，就會建立編輯器實例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。 如果編輯器支援多個視圖， `CreateEditorInstance` 則會同時建立檔資料和檔視圖物件。 如果檔資料物件已經開啟， `punkDocDataExisting` 則會傳遞非 null 值給 `IVsEditorFactory::CreateEditorInstance` 。 編輯器 factory 的執行必須透過查詢適當的介面來判斷現有的檔資料物件是否相容。 如需詳細資訊，請參閱 [支援多個檔的視圖](../extensibility/supporting-multiple-document-views.md)。

- 如果您使用簡化的內嵌方法，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面。

- 如果您決定要使用就地啟用，請執行下列介面：

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > `IOleInPlaceComponent`介面是用來避免 OLE 2 功能表合併。

   您的 `IOleCommandTarget` 執行會處理 **剪** 下、 **複製** 和 **貼** 上等命令。 在執行時 `IOleCommandTarget` ，決定您的編輯器是否需要自己的 *.vsct* 檔案來定義它自己的命令功能表結構，或者是否可以執行所定義的標準命令 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 一般而言，編輯器會使用並擴充 IDE 的功能表，並定義自己的工具列。 不過，除了使用 IDE 的標準命令集之外，編輯器通常還必須定義自己的特定命令。 您的編輯器必須宣告所使用的標準命令，然後在 *.vsct* 檔案中定義任何新的命令、內容功能表、最上層功能表和工具列。 如果您建立就地啟用編輯器，請 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> 在 *.vsct* 檔案中執行並定義編輯器的功能表和工具列，而不是使用 OLE 2 功能表合併。

- 若要防止 UI 中的功能表命令根本，您應該在發明新命令之前，先使用 IDE 中的現有命令。 共用命令定義于 *SharedCmdDef. .vsct* 和 *ShellCmdDef. .vsct* 中。 這些檔案預設會安裝在安裝的 VisualStudioIntegration\Common\Inc 子目錄中 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 。

- `ISelectionContainer` 可以表示單一和多重選取專案。 系統會將每個選取的物件實作為 `IDispatch` 物件。

- IDE 會實 `IOleUndoManager` 作為可從或可透過具現化的物件來存取的服務 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 。 您的編輯器會 `IOleUndoUnit` 針對每個動作來實行介面 `Undo` 。

- 有兩個位置可讓自訂編輯器公開 automation 物件：

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>請參閱

- [參與 automation 模型](../extensibility/internals/contributing-to-the-automation-model.md)