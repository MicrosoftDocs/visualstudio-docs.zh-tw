---
title: 如何：從檔移除 managed 程式碼擴充
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0832f0e404331e68fe88dfc990c51ed699eca263
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985786"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>如何：從檔移除 managed 程式碼擴充
  您可以透過程式設計的方式，從檔或活頁簿移除自訂群組件，這是 Microsoft Office Word 或 Microsoft Office Excel 的檔層級自訂的一部分。 使用者接著可以開啟檔並查看內容，但是您加入檔的任何自訂使用者介面（UI）都不會出現，而且您的程式碼也不會執行。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您可以使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供的其中一個 `RemoveCustomization` 方法來移除自訂群組件。 您所使用的方法取決於您是否想要在執行時間移除自訂（也就是在 Word 檔或 Excel 活頁簿開啟時，在自訂中執行程式碼），還是要從已關閉的檔或我所建立的檔中移除自訂在未安裝 Microsoft Office 的伺服器上。

## <a name="to-remove-the-customization-assembly-at-run-time"></a>若要在執行時間移除自訂群組件

1. 在您的自訂程式碼中，呼叫 <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> 方法（適用于 Word）或 <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> 方法（適用于 Excel）。 只有在不再需要自訂之後，才應該呼叫這個方法。

     您在程式碼中呼叫這個方法的位置，取決於您的自訂使用方式。 例如，如果客戶使用您的自訂功能，直到準備好將檔傳送給只需要檔本身（而非自訂）的其他用戶端時，您可以提供一些 UI，以在客戶按一下時呼叫 `RemoveCustomization`。 或者，如果您的自訂在第一次開啟時將資料填入檔，但自訂並未提供客戶直接存取的任何其他功能，則您可以在自訂之後立即呼叫 RemoveCustomization完成檔的初始化。

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>若要從已關閉的檔或伺服器上的檔移除自訂群組件

1. 在不需要 Microsoft Office （例如主控台應用程式或 Windows Forms 專案）的專案中，新增 VisualStudio 的參考。 *ServerDocument .dll*元件。

2. 在程式碼檔案的頂端新增下列**Imports**或**using**語句。

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. 呼叫 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別的靜態 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法，並指定參數的方案檔路徑。

     下列程式碼範例假設您要從桌上型電腦上名為*worddocument1.docx*的檔中移除自訂。

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. 建立專案，並在您想要移除自訂的電腦上執行應用程式。 電腦必須安裝適用于 Office runtime 的 Visual Studio 2010 工具。

## <a name="see-also"></a>請參閱
- [使用 ServerDocument 類別管理伺服器上的檔](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [如何：將 Managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
