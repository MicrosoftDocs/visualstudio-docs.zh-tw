---
title: 如何： 開啟編輯器開啟的文件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 621ed4436160b6f491abb34d8194c75595d9a54c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129802"
---
# <a name="how-to-open-editors-for-open-documents"></a>如何： 開啟編輯器開啟的文件
開啟文件視窗的專案之前，專案首先必須決定檔案是否已開啟另一個編輯器的文件視窗中。 可以在專案特定的編輯器中，請開啟檔案，或是其中一個標準的編輯器向[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="opening-a-project-specific-editor"></a>開啟專案的特定編輯器  
 您可以使用下列程序來開啟專案特定的編輯器已開啟的檔案。  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>若要開啟專案特定的編輯器開啟檔案  
  
1.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。  
  
     如果適當的話，這個呼叫會傳回指標的文件階層、 階層項目，和視窗框架。  
  
2.  如果文件開啟時，專案必須檢查是否只有文件資料物件存在，或如果文件檢視物件也會出現。  
  
    -   如果文件檢視物件存在，而此檢視在不同的階層或階層項目，專案會使用檢視的視窗框架的指標至 resurface 現有的視窗。  
  
    -   如果文件檢視物件存在，且此檢視位於相同的階層和階層項目中，專案可以開啟第二個檢視，如果它可以將附加至基礎的文件資料物件。 否則，專案應用於檢視的視窗框架指標 resurface 現有的視窗。  
  
    -   如果只有文件資料物件存在時，專案應該決定是否可以使用文件資料物件的檢視。 如果是相容的文件資料物件，完成步驟所述[開啟專案的特定編輯器](../extensibility/how-to-open-project-specific-editors.md)。  
  
     如果文件資料物件不相容，錯誤應該顯示給使用者，指出此檔案目前正使用中。 應該只會顯示此錯誤在暫時性情況下，例如，使用者時正在編譯檔案同時嘗試開啟檔案以外使用編輯器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文字編輯器。 核心文字編輯器可與編譯器共用文件資料物件。  
  
3.  如果文件尚未開啟，因為沒有任何文件資料物件或文件檢視物件，完成中的步驟[開啟專案的特定編輯器](../extensibility/how-to-open-project-specific-editors.md)。  
  
## <a name="opening-a-standard-editor"></a>開啟標準編輯器  
 請使用下列程序開啟的檔案已存在的標準編輯器開啟。  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>若要開啟的標準編輯器開啟檔案  
  
1.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
     這個方法會先驗證的文件尚未開啟藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>。 如果已開啟文件，則被 resurfaced 其編輯器視窗。  
  
2.  如果尚未開啟文件，然後完成中的步驟[如何： 開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 開啟專案的特定編輯器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何︰開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)