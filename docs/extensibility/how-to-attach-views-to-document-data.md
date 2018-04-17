---
title: 如何： 將附加至文件資料的檢視 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bcbb3e6b475a9dcd22d012073d3197013da337c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-views-to-document-data"></a>如何： 將附加至文件資料的檢視
如果您有新的文件檢視，您可以將它附加至現有的文件資料物件。  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>若要判斷是否可以將檢視附加至現有的文件資料物件  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  
  
2.  在您實作`IVsEditorFactory::CreateEditorInstance`，呼叫`QueryInterface`上現有的文件資料物件時，IDE 會呼叫您`CreateEditorInstance`實作。  
  
     呼叫`QueryInterface`可讓您檢查現有的文件資料物件，指定在`punkDocDataExisting`參數。  
  
     確切的介面，您必須查詢，不過，取決於正在開啟文件中，編輯器步驟 4 中所述。  
  
3.  如果找不到現有的文件資料物件上適當的介面，則傳回錯誤碼表示文件資料物件與您的編輯器不相容的編輯器。  
  
     在 IDE 的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，訊息方塊通知您已在其他編輯器中開啟文件，並詢問您想要將它關閉。  
  
4.  如果您關閉這份文件時，Visual Studio 會呼叫您的編輯器 factory 的第二次。 在呼叫時，`DocDataExisting`參數等於 NULL。 編輯器 factory 實作然後可以在您自己的編輯器中開啟文件資料物件。  
  
    > [!NOTE]
    >  若要判斷是否可以使用現有的文件資料物件，您也可以使用私用介面實作的知識轉型指標實際[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]私用實作的類別。 例如，所有標準編輯器實作`IVsPersistFileFormat`，後者繼承自<xref:Microsoft.VisualStudio.OLE.Interop.IPersist>。 因此，您可以呼叫`QueryInterface`如<xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>，以及在現有的文件資料物件上的類別識別碼是否符合您的實作類別識別碼，則您可以使用文件資料物件。  
  
## <a name="robust-programming"></a>穩固程式設計  
 當 Visual Studio 會呼叫您的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，它將傳遞回指標中的現有文件資料物件`punkDocDataExisting`參數，如果有的話。 檢查文件資料物件中傳回`punkDocDataExisting`來判斷文件資料物件是否適合您的編輯器，請注意，在本主題中的程序的步驟 4 中所述。 如果適合，則編輯器 factory 應該提供第二個檢視的資料中所述[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。 如果沒有，它應該會再顯示適當的錯誤訊息。  
  
## <a name="see-also"></a>請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [自訂編輯器中的文件資料和文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)