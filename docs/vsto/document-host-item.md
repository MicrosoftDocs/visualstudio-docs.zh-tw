---
title: 檔主專案
description: 瞭解檔主項目目是一種類型，可從 Word 的主要 interop 元件延伸檔案類型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 35455ac7751a34632362cfa3f2c9b8f2f827fc6d
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846905"
---
# <a name="document-host-item"></a>檔主專案
  <xref:Microsoft.Office.Tools.Word.Document> 主項目是一種類型，其會從 Word 的主要 Interop 組件擴充 <xref:Microsoft.Office.Interop.Word.Document> 類型。 <xref:Microsoft.Office.Tools.Word.Document> 主項目除了提供與 <xref:Microsoft.Office.Interop.Word.Document> 物件相同的所有屬性、方法和事件之外，也會公開其他事件，並做為主控制項和 Windows Forms 控制項的容器。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 文件層級專案中有代表專案中文件的預設 <xref:Microsoft.Office.Tools.Word.Document> 主項目。 在 VSTO 增益集專案中，您可以在執行階段產生 <xref:Microsoft.Office.Tools.Word.Document> 主項目。

## <a name="understand-the-document-host-item-in-document-level-projects"></a>瞭解檔層級專案中的檔主專案
 若要存取專案中的文件，請使用 `ThisDocument` 類別。 當您建立文件層級專案時，Visual Studio 會產生 `ThisDocument` 類別，做為 Word 和自訂程式碼之間的通訊連結。 `ThisDocument` 類別可讓您存取 <xref:Microsoft.Office.Tools.Word.Document> 主項目的成員，以在自訂中執行基本工作，例如在開啟或關閉文件時執行程式碼。 您也可以使用這些類別將控制項加入文件。 藉由合併不同的控制項集合並撰寫程式碼，您可以將控制項繫結至資料、從使用者收集資訊，以及回應使用者動作。 如需詳細資訊，請參閱 [程式檔層級自訂程式](../vsto/programming-document-level-customizations.md)。

 `ThisDocument` 類別提供了一個位置，供您開始在專案中撰寫程式碼。 由於該類別會提供與 Word 之主要 Interop 組件中的 <xref:Microsoft.Office.Interop.Word.Document> 物件相同的所有屬性、方法和事件，因此您也可以使用 `ThisDocument` 存取 Word 的物件模型。 如需詳細資訊，請參閱 [Word 物件模型總覽](../vsto/word-object-model-overview.md)。

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>檔層級專案中檔主專案的限制
 文件層級專案只能包含一個 <xref:Microsoft.Office.Tools.Word.Document> 主項目 (也就是 `ThisDocument` 類別)。 您無法在設計階段將新的 <xref:Microsoft.Office.Tools.Word.Document> 主項目加入專案，也無法在執行階段從文件層級自訂建立新的 <xref:Microsoft.Office.Tools.Word.Document> 主項目。

 如果您在執行階段建立新的 Word 文件，這個文件的類型將為 <xref:Microsoft.Office.Interop.Word.Document>。 由於這不是主項目，因此無法包含任何主控制項或 Windows Forms 控制項。 如需在執行時間建立檔的詳細資訊，請參閱 [如何：以程式設計方式建立新檔](../vsto/how-to-programmatically-create-new-documents.md)。

## <a name="understand-document-host-items-in-application-level-projects"></a>瞭解應用層級專案中的檔主專案
 在 VSTO 增益集專案中，您可以在執行階段為使用 Word 開啟的任何文件產生 <xref:Microsoft.Office.Tools.Word.Document> 主項目。 您可以使用 <xref:Microsoft.Office.Tools.Word.Document> 主項目將控制項加入相關聯的文件，或處理 <xref:Microsoft.Office.Interop.Word.Document> 物件上沒有的事件。

 若要產生 <xref:Microsoft.Office.Tools.Word.Document> 主項目，請使用 `GetVstoObject` 方法。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="see-also"></a>另請參閱
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
