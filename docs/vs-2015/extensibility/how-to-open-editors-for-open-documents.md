---
title: 如何：開啟開啟檔的編輯器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6e565e026ca49825a7b00a82e4e5c62a2f6c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204139"
---
# <a name="how-to-open-editors-for-open-documents"></a>如何︰針對開啟的文件開啟編輯器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

專案必須先判斷檔案是否已經在其他編輯器的文件視窗中開啟，專案才會開啟文件視窗。 您可以在專案特定的編輯器中開啟檔案，或在其中一個已註冊的標準編輯器中開啟檔案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
## <a name="opening-a-project-specific-editor"></a>開啟專案特定的編輯器  
 使用下列程式，針對已開啟的檔案開啟專案特定的編輯器。  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>開啟開啟檔案的專案特定編輯器  
  
1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。  
  
    此呼叫會傳回檔階層、階層專案和視窗框架的指標（如果有的話）。  
  
2. 如果檔是開啟的，專案就必須檢查檔資料物件是否存在，或者是否也有檔視圖物件存在。  
  
   - 如果檔視圖物件存在，而且此視圖適用于不同的階層或階層專案，則專案會使用視圖視窗框架的指標來 resurface 現有的視窗。  
  
   - 如果檔視圖物件存在，而且此視圖適用于相同的階層和階層專案，則專案可以附加至基礎檔資料物件，以開啟第二個視圖。 否則，專案應該使用視圖視窗框架的指標來 resurface 現有的視窗。  
  
   - 如果只有檔資料物件存在，專案應該判斷它是否可以使用檔資料物件來進行查看。 如果檔資料物件相容，請完成 [開啟專案特定編輯器](../extensibility/how-to-open-project-specific-editors.md)中所討論的步驟。  
  
     如果檔資料物件不相容，則應該向使用者顯示錯誤，指出檔案目前正在使用中。 此錯誤只應該在暫時性的情況下顯示，例如，當使用者嘗試使用核心文字編輯器以外的編輯器來開啟檔案時，檔案正在進行編譯的時間 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 核心文字編輯器可以與編譯器共用檔資料物件。  
  
3. 如果檔因為沒有檔資料物件或檔視圖物件而未開啟，請完成 [開啟專案特定編輯器](../extensibility/how-to-open-project-specific-editors.md)中的步驟。  
  
## <a name="opening-a-standard-editor"></a>開啟標準編輯器  
 使用下列程式，針對已開啟的檔案開啟標準編輯器。  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>開啟開啟檔案的標準編輯器  
  
1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
     這個方法會先確認檔尚未藉由呼叫來開啟 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 。 如果檔已經開啟，則會 resurfaced 其編輯器視窗。  
  
2. 如果檔未開啟，請完成 [如何：開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)中的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何：開啟專案特定的編輯器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何︰開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)
