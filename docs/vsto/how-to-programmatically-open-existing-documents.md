---
title: 如何：以程式設計方式開啟現有檔
description: 瞭解如何使用 Open 方法來開啟以完整路徑和檔案名指定的現有 Microsoft Word 檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525556"
---
# <a name="how-to-programmatically-open-existing-documents"></a>如何：以程式設計方式開啟現有檔
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法會開啟以完整路徑和檔案名指定的現有 Microsoft Office Word 檔。 這個方法會傳回 <xref:Microsoft.Office.Interop.Word.Document> 表示已開啟檔的。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>開啟檔

- 呼叫 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 集合的方法 <xref:Microsoft.Office.Interop.Word.Documents> ，並提供檔的路徑。

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>以唯讀方式開啟檔

- 呼叫 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 方法，提供檔的路徑，並在方法呼叫中將 *ReadOnly* 引數設定為 **True** 。

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>編譯程式碼
 這段程式碼範例需要下列項目：

- 名為 *NewDocument.doc* 的檔必須存在於磁片磁碟機 C 上名為 *Test* 的目錄中。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立新檔](../vsto/how-to-programmatically-create-new-documents.md)
- [如何：以程式設計方式關閉檔](../vsto/how-to-programmatically-close-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
