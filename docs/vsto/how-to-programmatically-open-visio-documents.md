---
title: HOW TO：以程式設計方式開啟 Visio 文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1815b0f336026890c88ec0794ea72911560ecb38
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875718"
---
# <a name="how-to-programmatically-open-visio-documents"></a>HOW TO：以程式設計方式開啟 Visio 文件
  有兩種方法來開啟現有的 Microsoft Office Visio 文件：開啟和 OpenEx。 OpenEx 方法等同於開放式的方法，不同之處在於它會提供在其中呼叫端可以指定如何在文件開啟時的引數。  
  
 如需此物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) 方法的 VBA 參考文件。  
  
## <a name="open-a-visio-document"></a>開啟 Visio 文件  
  
### <a name="to-open-a-visio-document"></a>開啟 Visio 文件  
  
-   呼叫 `Microsoft.Office.Interop.Visio.Documents.Open` 方法並提供 Visio 文件的完整路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>使用指定的引數開啟 Visio 文件  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>開啟 Visio 文件為唯讀並停駐  
  
-   呼叫 `Microsoft.Office.Interop.Visio.Documents.OpenEx` 方法，提供 Visio 文件的完整路徑，以及包含要使用的引數，在本例中為「停駐」和「唯讀」。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   名為 Visio 文件`myDrawing.vsd`必須位於名為`Test`中*我的文件*資料夾 （適用於 Windows XP 及更早版本） 或*文件*（適用於 Windows Vista) 的資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何：以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
