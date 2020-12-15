---
title: 如何：從檔中移除 managed 程式碼延伸模組
description: 以程式設計方式從 Microsoft Word 或 Excel 檔層級自訂一部分的檔或活頁簿中移除自訂群組件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be32109e2a34df8605c0dbe5ba9f1df4e32cfc55
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524464"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>如何：從檔中移除 managed 程式碼延伸模組
  您可以用程式設計的方式，從檔或活頁簿（Microsoft Office Word 或 Microsoft Office Excel 的檔層級自訂中）移除自訂群組件。 使用者接著可以開啟檔並查看內容，但您新增至檔的任何自訂使用者介面 (UI) 不會出現，而且您的程式碼將不會執行。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您可以使用所提供的其中一種方法來移除自訂群組件 `RemoveCustomization` [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 您要使用哪一種方法取決於您是否要在執行時間移除自訂 (也就是在 Word 檔或 Excel 活頁簿開啟) 時執行自訂中的程式碼，或者，如果您想要從關閉的檔或未安裝 Microsoft Office 的伺服器上的檔中移除自訂。

## <a name="to-remove-the-customization-assembly-at-run-time"></a>若要在執行時間移除自訂群組件

1. 在您的自訂程式碼中，呼叫 <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> Word) 的方法 (或 <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> Excel) 的方法 (。 只有在不再需要自訂之後，才應該呼叫這個方法。

     當您在程式碼中呼叫這個方法時，將視您的自訂使用方式而定。 例如，如果客戶使用您自訂的功能，直到準備好將檔傳送給其他只需要檔本身的用戶端 (而不是自訂) 時，您可以提供一些在 `RemoveCustomization` 客戶按一下時呼叫的 UI。 或者，如果您的自訂是在第一次開啟資料時填入檔，但自訂並未提供客戶直接存取的任何其他功能，則您可以在自訂完成初始化檔時立即呼叫 RemoveCustomization。

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>從伺服器上的已關閉檔或檔移除自訂群組件

1. 在不需要 Microsoft Office 的專案中（例如主控台應用程式或 Windows Forms 專案），加入 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* 元件的參考。

2. 將下列 **Imports** 或 **using** 語句加入至程式碼檔案的頂端。

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. 呼叫類別的靜態 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> ，並指定參數的方案檔路徑。

     下列程式碼範例假設您要從桌上型電腦上名為 *WordDocument1.docx* 的檔移除自訂。

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. 建立專案，並在您想要移除自訂的電腦上執行應用程式。 電腦必須安裝 Visual Studio 2010 Tools for Office runtime。

## <a name="see-also"></a>另請參閱
- [使用 ServerDocument 類別管理伺服器上的檔](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [如何：將 Managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
