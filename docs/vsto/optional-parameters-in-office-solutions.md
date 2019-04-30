---
title: Office 方案中的選擇性參數
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8684ad4b9429a5499660ef4ad6fdd8133dccaa5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442407"
---
# <a name="optional-parameters-in-office-solutions"></a>Office 方案中的選擇性參數
  Microsoft Office 應用程式物件模型中的許多方法，都接受選擇性參數。 如果您使用 Visual Basic 在 Visual Studio 中開發 Office 方案，就不必傳遞選擇性參數的值，因為每個遺漏的參數都會自動使用預設值。 在大部分情況下，您也可以省略 Visual C# 專案中的選擇性參數。 不過，您不能省略選擇性**ref**參數的`ThisDocument`文件層級 Word 專案中的類別。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 如需有關使用 Visual C# 和 Visual Basic 專案中的選擇性參數的詳細資訊，請參閱[具名和選擇性引數&#40;C&#35;程式設計指南&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments)並[&#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)。

> [!NOTE]
> 在舊版的 Visual Studio 中，您必須為 Visual C# 專案中的每一個選擇性參數傳遞值。 為方便起見，這些專案包含名為 `missing` 的全域變數，當您想要使用參數的預設值時，可以傳遞給選擇性參數。 Visual C# 專案適用於 Office 的 Visual Studio 仍然包含`missing`變數，但您通常不需要您在開發中的 Office 方案時，請使用它[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]，但當您呼叫方法的選擇性**ref**中的參數`ThisDocument`Word 的文件層級專案中的類別。

## <a name="example-in-excel"></a>Excel 範例
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法有許多選擇性參數。 某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。 這個範例需要有名為 `Sheet1` 工作表類別的文件層級專案。

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Word 範例
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法有許多選擇性參數。 某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>ThisDocument 類別，在 Visual C# 文件層級專案中使用方法選擇性的參數 word
 Word 物件模型包含許多方法，使用選擇性**ref**可接受的參數<xref:System.Object>值。 不過，您不能省略選擇性**ref**產生的方法參數的`ThisDocument`word Visual C# 文件層級專案中的類別。 Visual C# 可讓您略過選擇性**ref**不類別的介面方法的參數。 例如，下列程式碼範例無法編譯，因為您不能省略選擇性**ref**的參數<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>方法`ThisDocument`類別。

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 當您呼叫 `ThisDocument` 類別的方法時，請遵循這些指導方針：

- 若要接受預設值的選擇性**ref**參數，傳遞`missing`變數設為參數。 在 Visual C# Office 專案中，`missing` 變數會自動定義並指派給產生的專案程式碼中的值 <xref:System.Type.Missing>。

- 若要指定您自己的值的選擇性**ref**參數，宣告指派給您想要指定，值的物件，並接著將物件傳遞至參數。

  下列程式碼範例示範如何呼叫<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>方法，藉由指定的值*用於儲存 ignoreUppercase*參數並接受其他參數的預設值。

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  如果您想要撰寫程式碼，會省略選擇性**ref**中方法的參數`ThisDocument`類別，您可以另外呼叫相同的方法上<xref:Microsoft.Office.Interop.Word.Document>所傳回的物件<xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A>屬性，並略過來自該方法的參數。 您可以執行這項操作的原因是，<xref:Microsoft.Office.Interop.Word.Document> 是介面不是類別。

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  如需值和參考型別參數的詳細資訊，請參閱[值和傳參考方式傳遞引數&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) （適用於 Visual Basic) 和[傳遞參數&#40;C&#35;程式設計指南&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。

## <a name="see-also"></a>另請參閱
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
