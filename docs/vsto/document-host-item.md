---
title: "文件主項目 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de243ee4b36d180b93e1b64f2a08c013a05d5360
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="document-host-item"></a>Document 主項目
  <xref:Microsoft.Office.Tools.Word.Document> 主項目是一種類型，其會從 Word 的主要 Interop 組件擴充 <xref:Microsoft.Office.Interop.Word.Document> 類型。 <xref:Microsoft.Office.Tools.Word.Document> 主項目除了提供與 <xref:Microsoft.Office.Interop.Word.Document> 物件相同的所有屬性、方法和事件之外，也會公開其他事件，並做為主控制項和 Windows Forms 控制項的容器。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 文件層級專案中有代表專案中文件的預設 <xref:Microsoft.Office.Tools.Word.Document> 主項目。 在 VSTO 增益集專案中，您可以在執行階段產生 <xref:Microsoft.Office.Tools.Word.Document> 主項目。  
  
## <a name="understanding-the-document-host-item-in-document-level-projects"></a>了解文件層級專案中的 Document 主項目  
 若要存取專案中的文件，請使用 `ThisDocument` 類別。 當您建立文件層級專案時，Visual Studio 會產生 `ThisDocument` 類別，做為 Word 和自訂程式碼之間的通訊連結。 `ThisDocument` 類別可讓您存取 <xref:Microsoft.Office.Tools.Word.Document> 主項目的成員，以在自訂中執行基本工作，例如在開啟或關閉文件時執行程式碼。 您也可以使用這些類別將控制項加入文件。 藉由合併不同的控制項集合並撰寫程式碼，您可以將控制項繫結至資料、從使用者收集資訊，以及回應使用者動作。 如需詳細資訊，請參閱 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)。  
  
 `ThisDocument` 類別提供了一個位置，供您開始在專案中撰寫程式碼。 由於該類別會提供與 Word 之主要 Interop 組件中的 <xref:Microsoft.Office.Interop.Word.Document> 物件相同的所有屬性、方法和事件，因此您也可以使用 `ThisDocument` 存取 Word 的物件模型。 如需詳細資訊，請參閱 [Word Object Model Overview](../vsto/word-object-model-overview.md)。  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>文件層級專案中 Document 主項目的限制  
 文件層級專案只能包含一個 <xref:Microsoft.Office.Tools.Word.Document> 主項目 (也就是 `ThisDocument` 類別)。 您無法在設計階段將新的 <xref:Microsoft.Office.Tools.Word.Document> 主項目加入專案，也無法在執行階段從文件層級自訂建立新的 <xref:Microsoft.Office.Tools.Word.Document> 主項目。  
  
 如果您在執行階段建立新的 Word 文件，這個文件的類型將為 <xref:Microsoft.Office.Interop.Word.Document>。 由於這不是主項目，因此無法包含任何主控制項或 Windows Form 控制項。 如需有關如何在執行階段建立文件的詳細資訊，請參閱[How to： 以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)。  
  
## <a name="understanding-document-host-items-in-application-level-projects"></a>了解應用程式層級專案中的 Document 主項目  
 在 VSTO 增益集專案中，您可以在執行階段為使用 Word 開啟的任何文件產生 <xref:Microsoft.Office.Tools.Word.Document> 主項目。 您可以使用 <xref:Microsoft.Office.Tools.Word.Document> 主項目將控制項加入相關聯的文件，或處理 <xref:Microsoft.Office.Interop.Word.Document> 物件上沒有的事件。  
  
 若要產生<xref:Microsoft.Office.Tools.Word.Document>主項目，請使用 GetVstoObject 方法。 如需詳細資訊，請參閱 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  