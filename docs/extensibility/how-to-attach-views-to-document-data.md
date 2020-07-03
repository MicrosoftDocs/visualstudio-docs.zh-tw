---
title: 如何：將視圖附加至檔資料 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5437e3a5d4fb0d6d33d570eb4d8923245cb287b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905889"
---
# <a name="how-to-attach-views-to-document-data"></a>如何：將視圖附加至檔資料
如果您有新的檔視圖，您可以將它附加到現有的檔資料物件。

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>判斷您是否可以將視圖附加至現有的檔資料物件

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。

2. 在您的執行中 `IVsEditorFactory::CreateEditorInstance` ， `QueryInterface` 當 IDE 呼叫您的執行時，在現有的檔資料物件上呼叫 `CreateEditorInstance` 。

    呼叫可 `QueryInterface` 讓您檢查在參數中指定的現有檔資料物件 `punkDocDataExisting` 。

    不過，您必須查詢的確切介面取決於開啟檔的編輯器，如步驟4中所述。

3. 如果您在現有的檔資料物件上找不到適當的介面，則會將錯誤碼傳回您的編輯器，指出檔資料物件與您的編輯器不相容。

    在 IDE 的執行中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ，訊息方塊會通知您檔已在另一個編輯器中開啟，並詢問您是否要將它關閉。

4. 如果您關閉此檔，則 Visual Studio 會第二次呼叫您的編輯器 factory。 在此呼叫中， `DocDataExisting` 參數等於 Null。 然後，您的編輯器工廠就可以在您自己的編輯器中開啟檔資料物件。

   > [!NOTE]
   > 若要判斷您是否可以使用現有的檔資料物件，您也可以將指標轉型為私用實值的實體類別，藉此使用介面實作用的私用知識 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 。 例如，所有標準編輯器都會執行 `IVsPersistFileFormat` ，其繼承自 <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> 。 因此，您可以呼叫 `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> ，如果現有檔資料物件上的類別 id 符合您的實作為類別 id，則您可以使用檔資料物件。

## <a name="robust-programming"></a>穩固程式設計
 當 Visual Studio 呼叫方法的執行時 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ，它會傳回參數中現有檔資料物件的指標 `punkDocDataExisting` （如果有的話）。 檢查中傳回的檔資料物件 `punkDocDataExisting` ，以判斷檔資料物件是否適用于您的編輯器，如本主題中程式的步驟4中的附注所述。 如果適合，則您的編輯器 factory 應該提供資料的第二個視圖，如[支援多個檔視圖](../extensibility/supporting-multiple-document-views.md)中所述。 如果不是，則應該顯示適當的錯誤訊息。

## <a name="see-also"></a>另請參閱
- [支援多個檔視圖](../extensibility/supporting-multiple-document-views.md)
- [自訂編輯器中的檔資料和檔視圖](../extensibility/document-data-and-document-view-in-custom-editors.md)
