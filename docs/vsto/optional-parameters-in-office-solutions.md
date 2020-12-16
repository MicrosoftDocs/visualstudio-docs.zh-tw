---
title: Office 方案中的選擇性參數
description: 瞭解如何不需要傳遞選擇性參數的值，因為每個遺漏的參數都會自動使用預設值。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7567f43dfa79e6a1e5d92b9ecddbf7918a6edef3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527569"
---
# <a name="optional-parameters-in-office-solutions"></a>Office 方案中的選擇性參數
  Microsoft Office 應用程式物件模型中的許多方法，都接受選擇性參數。 如果您使用 Visual Basic 在 Visual Studio 中開發 Office 方案，就不必傳遞選擇性參數的值，因為每個遺漏的參數都會自動使用預設值。 在大部分的情況下，也可以省略 Visual C# 專案中的選擇性參數。 不過，您無法 `ThisDocument` 在檔層級 Word 專案中省略類別的選擇性 ref 參數。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 如需在 Visual c # 和 Visual Basic 專案中使用選擇性參數的詳細資訊，請參閱 [&#40;C&#35; 程式設計指南&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) 和 [選擇性參數 &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;的命名和選擇性引數。

> [!NOTE]
> 在舊版的 Visual Studio 中，您必須為 Visual C# 專案中的每一個選擇性參數傳遞值。 為方便起見，這些專案包含名為 `missing` 的全域變數，當您想要使用參數的預設值時，可以傳遞給選擇性參數。 適用于 Office Visual Studio 的 Visual c # 專案仍包含 `missing` 變數，但在中開發 office 方案時，您通常不需要使用它 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ，除非您在 `ThisDocument` Word 檔層級專案的類別中，以選擇性 ref 參數呼叫方法。

## <a name="example-in-excel"></a>Excel 範例
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法有許多選擇性參數。 某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。 這個範例需要有名為 `Sheet1` 工作表類別的文件層級專案。

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Word 範例
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法有許多選擇性參數。 某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>在 Word 的 Visual c # 檔層級專案中，于 ThisDocument 類別中使用方法的選擇性參數
 Word 物件模型包含許多具有可接受值之選擇性 **ref** 參數的方法 <xref:System.Object> 。 不過，您無法 `ThisDocument` 在 Word 的 Visual c # 檔層級專案中，省略所產生類別之方法的選擇性 ref 參數。 Visual c # 可讓您只針對介面的方法（而非類別）省略選擇性的 **ref** 參數。 例如，下列程式碼範例不會進行編譯，因為您不能省略類別的方法的選擇性 **ref** 參數 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> `ThisDocument` 。

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 當您呼叫 `ThisDocument` 類別的方法時，請遵循這些指導方針：

- 若要接受選擇性 **ref** 參數的預設值，請將 `missing` 變數傳遞給參數。 在 Visual C# Office 專案中，`missing` 變數會自動定義並指派給產生的專案程式碼中的值 <xref:System.Type.Missing>。

- 若要為選擇性 **ref** 參數指定您自己的值，請宣告指派給您想要指定之值的物件，然後將物件傳遞給參數。

  下列程式碼範例示範如何藉 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> 由指定 *ignoreUppercase* 參數的值，以及接受其他參數的預設值，來呼叫方法。

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  如果您想要撰寫程式碼來省略類別中方法的選擇性 **ref** 參數 `ThisDocument` ，您也可以在屬性傳回的物件上呼叫相同的方法 <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> ，並省略該方法中的參數。 您可以執行這項操作的原因是，<xref:Microsoft.Office.Interop.Word.Document> 是介面不是類別。

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  如需有關值和參考型別參數的詳細資訊，請參閱以 [傳值方式傳遞引數，並以傳址方式 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic [C) 程式設計手冊 &#40;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。

## <a name="see-also"></a>另請參閱
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
