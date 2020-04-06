---
title: 演練:向自定義編輯器添加功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697782"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>演練:向自訂編輯器新增功能
建立自定義編輯器後,可以向其添加更多功能。

## <a name="to-create-an-editor-for-a-vspackage"></a>建立 VS 套件建立編輯器

1. 使用可視化工作室包專案範本創建自定義編輯器。

     有關詳細資訊,請參閱[演練:建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。

2. 確定是希望編輯器支援單個檢視還是多個檢視。

     支援 **「新建視窗」** 命令或具有表單檢視和代碼檢視的編輯器需要單獨的文件資料物件和文件檢視物件。 在僅支援單個檢視的編輯器中,文檔數據物件和文檔檢視物件可以在同一對象上實現。

     有關多個檢視的範例,請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。

3. 通過設置<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面實現編輯器工廠。

     有關詳細資訊,請參閱[編輯器工廠](../extensibility/editor-factories.md)。

4. 確定是希望編輯器使用就地激活還是簡化嵌入來管理文檔檢視物件視窗。

     簡化的嵌入編輯器視窗承載標準文件檢視,而就地啟動編輯器視窗將 ActiveX 控制件或其他活動物件作為文檔檢視。 有關詳細資訊,請參閱[簡化嵌入](../extensibility/simplified-embedding.md)與[就地啟動](/visualstudio/misc/in-place-activation?view=vs-2015)。

5. 實現介面<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>來處理命令。

6. 提供文件持久性和對外部檔案變更的回應:

    1. 要保留該檔,請實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>的文件數據物件。

    2. 要回應外部檔更改,請實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>的文檔數據物件並在其上實現。

        > [!NOTE]
        > 調用`QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>以獲取`IVsFileChangeEx`指向的指標。

7. 使用原始碼控制協調文件編輯事件。 請遵循下列步驟：

    1. 通過調用`IVsQueryEditQuerySave2``QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>獲取指向 的指標。

    2. 當發生第一個編輯事件時,<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>調用 方法。

         此方法會提示使用者簽出該檔(如果該檔尚未簽出)。請務必處理「檔未簽出」條件以避免錯誤。

    3. 同樣,在保存檔之前,調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>方法。

         此方法會提示使用者保存檔(如果該檔尚未保存或自上次保存以來已更改)。

8. 使 **「屬性」** 視窗能夠顯示編輯器中選擇的文本的屬性。 請遵循下列步驟：

    1. 每次<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>文字選擇更改時調用 ,傳入<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>您的實現 中。

    2. 調用`QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服務 以<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>獲取指向的指標。

9. 允許使用者在編輯器和**工具箱**之間,或在外部編輯器(如 Microsoft Word)和**工具箱**之間拖放專案。 請遵循下列步驟：

    1. 在`IDropTarget`編輯器上實現,以提醒 IDE 編輯器是放置目標。

    2. 在檢視<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>上實現介面,以便編輯器可以啟用和禁用**工具箱**中的專案。

    3. 實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>並調`QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>用 服務以<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>獲取<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>指向和介面的指標。

         這些步驟讓 VSPackage 能夠將新專案加入**工具箱**。

10. 決定是否需要編輯器的任何其他可選功能。

    - 如果希望編輯器支援尋找與取代命令,請實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>。

    - 如果要在編輯器中使用文件大綱工具視窗,請實現`IVsDocOutlineProvider`。

    - 如果要在<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>編輯器中使用狀態列,請實現和調`QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>用 以`IVsStatusBar`獲取指向 的指標。

         例如,編輯器可以顯示列/列資訊、選擇模式(流/框)和插入模式(插入/過度擊)。

    - 如果希望編輯器支援該`Undo`命令,建議的方法是使用 OLE 撤銷管理器模型。 作為替代方法,您可以讓編輯器直接處理該`Undo`命令。

11. 創建註冊表資訊,包括 VSPackage 的 GUID、功能表、編輯器和其他功能。

     下面是一個通用代碼示例,您將在 *.rgs*檔腳本中放置這些代碼,以演示如何正確註冊編輯器。

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

12. 實施上下文相關的説明支援。

     此步驟允許您為編輯器中的專案提供 F1 説明和動態幫助視窗支援。 有關詳細資訊,請參閱[如何:為編輯器提供上下文](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015)。

13. 通過實現介面,`IDispatch`從編輯器中公開自動化物件模型。

     如需詳細資訊，請參閱 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)。

## <a name="robust-programming"></a>穩固程式設計

- 當 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>調用 方法時,將創建編輯器實例。 如果編輯器支援多個檢視,`CreateEditorInstance`則同時創建文檔資料和文檔檢視物件。 如果文件資料物件已開啟,則將非空`punkDocDataExisting`值傳遞給`IVsEditorFactory::CreateEditorInstance`。 編輯器工廠實現必須通過查詢現有文件數據物件上的相應介面來確定其是否相容。 有關詳細資訊,請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。

- 如果使用簡化的嵌入方法,則<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>實現介面。

- 如果您決定使用就地啟動,實現以下介面:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > 該`IOleInPlaceComponent`介面用於避免 OLE 2 功能表合併。

   您`IOleCommandTarget`可以執行, 請**將剪切**、**複製**與**貼上**。 實現`IOleCommandTarget`時,決定編輯器是否需要自己的 *.vsct*檔來定義自己的命令功能表結構,或者是否可以[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實現 定義的標準命令。 通常,編輯人員使用並擴展 IDE 的功能表並定義自己的工具列。 但是,編輯器除了使用 IDE 的標準命令集外,通常還需要定義自己的特定命令。 編輯器必須聲明它使用的標準命令,然後在 *.vsct*檔中定義任何新命令、上下文菜單、頂級功能表和工具列。 如果建立就地啟動編輯器,請實現<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>和定義 *.vsct*檔案中編輯器的功能表和工具列,而不是使用 OLE 2 選單合併。

- 為了防止功能表命令在 UI 中擁擠,在發明新命令之前,應使用 IDE 中的現有命令。 共用命令在*SharedCmdDef.vsct*和*ShellCmdDef.vsct 中*定義。 這些檔預設安裝在安裝[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]的 VisualStudio 整合_Common_Inc子目錄中。

- `ISelectionContainer`可以同時表示單選和多個選擇。 每個選定的物件都作為對`IDispatch`象 實現。

- IDE`IOleUndoManager`可從<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>或 做物件可實例化的物件的服務<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>。 編輯器實現每個`Undo`操作`IOleUndoUnit`的介面。

- 自訂編輯器可以公開自動化物件,有兩個位置:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>另請參閱

- [為自動化模型做出貢獻](../extensibility/internals/contributing-to-the-automation-model.md)
