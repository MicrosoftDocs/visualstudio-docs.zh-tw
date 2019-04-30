---
title: HOW TO：以程式設計方式開啟現有文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 490dda6e5357cd0933c6a8b494cc4373038e5c1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812379"
---
# <a name="how-to-programmatically-open-existing-documents"></a>HOW TO：以程式設計方式開啟現有文件
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法會開啟完整的路徑和檔案名稱所指定的現有 Microsoft Office Word 文件。 這個方法會傳回<xref:Microsoft.Office.Interop.Word.Document>表示開啟的文件。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>若要開啟的文件

- 呼叫<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法的<xref:Microsoft.Office.Interop.Word.Documents>集合，並提供文件的路徑。

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>若要開啟 文件標記為唯讀

- 呼叫<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法，提供路徑給文件，並設定*ReadOnly*引數**True**方法呼叫中。

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>編譯程式碼
 這個程式碼範例需要下列項目：

- 名為文件*NewDocument.doc*必須存在於一個名為目錄*測試*上磁碟機 c。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)
- [如何：以程式設計方式關閉文件](../vsto/how-to-programmatically-close-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
