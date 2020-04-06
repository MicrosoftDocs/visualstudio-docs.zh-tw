---
title: 如何:將檢視附加到文件數據 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711081"
---
# <a name="how-to-attach-views-to-document-data"></a>如何:將檢視附加到文件資料
如果您有新的文檔檢視,則可以將其附加到現有文檔資料物件。

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>確定是否可以將檢視附加到現有文件資料物件

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。

2. 在實現`IVsEditorFactory::CreateEditorInstance`中`QueryInterface`,當 IDE`CreateEditorInstance`調用您的 實現時調用現有文檔數據物件。

    呼叫`QueryInterface`讓您能夠檢查現有文件資料物件,該物件在`punkDocDataExisting`參數中 指定。

    但是,您必須查詢的確切介面取決於打開文檔的編輯器,如步驟 4 中所述。

3. 如果在現有文件數據物件上找不到適當的介面,則向編輯器返回錯誤代碼,指示文檔數據物件與編輯器不相容。

    在 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>的 實現中,一個訊息框會通知您文檔在另一個編輯器中處於打開狀態,並詢問您是否要關閉它。

4. 如果關閉此文件,則 Visual Studio 會第二次調用編輯器工廠。 在此呼叫中,`DocDataExisting`參數等於 NULL。 然後,編輯器工廠實現可以在您自己的編輯器中打開文檔數據物件。

   > [!NOTE]
   > 要確定是否可以使用現有文檔數據物件,還可以通過強制將指標強制轉換到私有實現的實際[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]類來使用介面實現的私有知識。 例如,所有標準編輯器實現`IVsPersistFileFormat`從繼承<xref:Microsoft.VisualStudio.OLE.Interop.IPersist>。 因此,您可以調用`QueryInterface`<xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>,如果現有文檔資料物件的類 ID 與實現的類 ID 匹配,則可以使用文檔數據物件。

## <a name="robust-programming"></a>穩固程式設計
 當 Visual Studio<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>調用方法 的實現時,`punkDocDataExisting`它會傳遞指向 參數中現有文檔數據物件的指標(如果存在)。 檢查傳`punkDocDataExisting`回的文件資料物件,以確定文件資料物件是否適合您的編輯器,本主題中的步驟 4 中的註釋中所述。 如果合適,則編輯器工廠應提供[支援多個文檔視圖](../extensibility/supporting-multiple-document-views.md)中概述的數據的第二個檢視。 如果沒有,則它應該顯示相應的錯誤消息。

## <a name="see-also"></a>另請參閱
- [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)
- [自訂編輯器中的文件資料與文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)
