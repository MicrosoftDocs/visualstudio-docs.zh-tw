---
title: 如何：針對開啟的檔開啟編輯器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f67a7fad5944e82087f520508ef9f4a66b7109d
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905814"
---
# <a name="how-to-open-editors-for-open-documents"></a>如何：針對開啟的檔開啟編輯器
專案在開啟文件視窗之前，必須先判斷檔案是否已經在另一個編輯器的文件視窗中開啟。 檔案可以在專案特定的編輯器中開啟，或使用已向註冊的其中一個標準編輯器 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="open-a-project-specific-editor"></a>開啟專案特定的編輯器
 使用下列程式，針對已開啟的檔案開啟專案特定的編輯器。

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>若要開啟開啟檔案的專案特定編輯器

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。

    此呼叫會傳回檔階層、階層專案和視窗框架的指標（如果適用的話）。

2. 如果檔已開啟，則專案必須檢查是否只有檔資料物件存在，或檔視圖物件是否也存在。

   - 如果檔視圖物件存在，而此視圖適用于不同的階層或階層專案，則專案會使用此視圖視窗框架的指標來 resurface 現有的視窗。

   - 如果檔視圖物件存在，且此視圖適用于相同的階層和階層專案，則專案可以附加至基礎檔資料物件，以開啟第二個視圖。 否則，專案應該使用視圖視窗框架的指標來 resurface 現有的視窗。

   - 如果只有檔資料物件存在，專案應該決定是否可以使用檔資料物件來進行其視圖。 如果檔資料物件相容，請完成[開啟專案特定編輯器](../extensibility/how-to-open-project-specific-editors.md)中所討論的步驟。

     如果檔資料物件不相容，則會向使用者顯示錯誤，指出該檔案目前正在使用中。 這個錯誤應該只會在暫時性的情況下顯示，例如，當使用者嘗試使用核心文字編輯器以外的編輯器來開啟檔案時，同時編譯檔案的時間 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 核心文字編輯器可以與編譯器共用檔資料物件。

3. 如果檔因為沒有檔資料物件或檔視圖物件而未開啟，請完成[開啟專案特定編輯器](../extensibility/how-to-open-project-specific-editors.md)中的步驟。

## <a name="open-a-standard-editor"></a>開啟標準編輯器
 使用下列程式，針對已開啟的檔案開啟標準編輯器。

### <a name="to-open-a-standard-editor-for-an-open-file"></a>為開啟的檔案開啟標準編輯器

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。

     這個方法會先確認檔尚未藉由呼叫來開啟 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 。 如果檔已開啟，則會 resurfaced 其編輯器視窗。

2. 如果檔未開啟，請完成[如何：開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)中的步驟。

## <a name="see-also"></a>另請參閱
- [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟專案特定的編輯器](../extensibility/how-to-open-project-specific-editors.md)
- [如何：開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)
