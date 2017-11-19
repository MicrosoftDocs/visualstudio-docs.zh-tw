---
title: "Office 方案中的選擇性參數 |Microsoft 文件"
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
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4293d13ffc5b69c23c0b613a3d9747248d6fa790
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="optional-parameters-in-office-solutions"></a>Office 方案中的選擇性參數
  Microsoft Office 應用程式物件模型中的許多方法，都接受選擇性參數。 如果您使用 Visual Basic 在 Visual Studio 中開發 Office 方案，就不必傳遞選擇性參數的值，因為每個遺漏的參數都會自動使用預設值。 在大部分情況下，您也可以省略 Visual C# 專案中的選擇性參數。 不過，您不能省略選擇性**ref**參數`ThisDocument`文件層級 Word 專案中的類別。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如需有關使用 Visual C# 和 Visual Basic 專案中的選擇性參數的詳細資訊，請參閱[具名和選擇性引數 &#40;& #35。程式設計手冊 &#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments)和[選擇性參數 &#40;Visual Basic &#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  在舊版的 Visual Studio 中，您必須為 Visual C# 專案中的每一個選擇性參數傳遞值。 為方便起見，這些專案包含名為 `missing` 的全域變數，當您想要使用參數的預設值時，可以傳遞給選擇性參數。 Visual C# 專案的 Visual Studio 中的 Office，仍然包含`missing`變數，但您通常不需要開發中的 Office 方案時使用它[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]，除了當您呼叫方法的選擇性**ref**中的參數`ThisDocument`Word 的文件層級專案中的類別。  
  
## <a name="example-in-excel"></a>Excel 範例  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法有許多選擇性參數。 某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。 這個範例需要有名為 `Sheet1` 工作表類別的文件層級專案。  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Word 範例  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法有許多選擇性參數。 某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="using-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>在 Word Visual C# 文件層級專案中使用 ThisDocument 類別中的方法選擇性參數  
 Word 物件模型包含許多方法可選擇**ref**接受的參數<xref:System.Object>值。 不過，您不能省略選擇性**ref**產生方法參數的`ThisDocument`Visual C# 文件層級 Word 專案中的類別。 Visual C# 可讓您省略選擇性**ref**不類別的介面，方法的參數。 例如，下列程式碼範例無法編譯，因為您不能省略選擇性**ref**參數<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>方法`ThisDocument`類別。  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 當您呼叫 `ThisDocument` 類別的方法時，請遵循這些指導方針：  
  
-   若要接受選擇性的預設值**ref**參數，傳遞`missing`變數設為參數。 在 Visual C# Office 專案中，`missing` 變數會自動定義並指派給產生的專案程式碼中的值 <xref:System.Type.Missing>。  
  
-   若要指定您自己的選擇性值**ref**參數，宣告物件指派給您想要指定的值，並再將物件傳遞至參數。  
  
 下列程式碼範例示範如何呼叫<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>方法藉由指定的值*ignoreUppercase*參數並接受其他參數的預設值。  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
 如果您想要撰寫程式碼，會省略選擇性**ref**中方法的參數`ThisDocument`類別，您可以上另行呼叫相同方法<xref:Microsoft.Office.Interop.Word.Document>所傳回物件<xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A>屬性，並省略來自該方法的參數。 您可以執行這項操作的原因是，<xref:Microsoft.Office.Interop.Word.Document> 是介面不是類別。  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
 如需值和參考型別參數的詳細資訊，請參閱[傳遞引數傳值和依參考 &#40;Visual Basic &#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) （適用於 Visual Basic) 和[傳遞參數 &#40;& #35。程式設計手冊 &#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>另請參閱  
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  