---
title: 如何： 以程式設計方式關閉 Visio 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d800fbe0a6dda6fc7c5160d607d393afcb920cd9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671569"
---
# <a name="how-to-programmatically-close-visio-documents"></a>如何： 以程式設計方式關閉 Visio 文件
  您可以使用 `Microsoft.Office.Interop.Visio.Document.Close` 方法來關閉使用中的 Microsoft Office Visio 文件。  
  
 如需這個方法的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) 方法的 VBA 參考文件。  
  
## <a name="close-the-active-document"></a>關閉使用中的文件  
  
### <a name="to-close-the-active-document"></a>關閉使用中的文件  
  
-   呼叫 `Microsoft.Office.Interop.Visio.Document.Close` 方法，關閉使用中的文件。  
  
     若要使用下列程式碼範例，在中執行`ThisAddIn`適用於 Visio VSTO 增益集專案中的類別。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何： 以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  