---
title: 如何： 以程式設計方式快取 Office 文件中的資料來源
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89aef81c68b95947215142ddadf9081d49aa95b2
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256701"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>如何： 以程式設計方式快取 Office 文件中的資料來源
  您以程式設計的方式可以將文件中的資料快取資料物件，藉由呼叫`StartCaching`方法的許多項目，例如<xref:Microsoft.Office.Tools.Word.Document>， <xref:Microsoft.Office.Tools.Excel.Workbook>，或<xref:Microsoft.Office.Tools.Excel.Worksheet>。 移除資料快取中的資料物件，藉由呼叫`StopCaching`主項目的的方法。  
  
 `StartCaching`方法和`StopCaching`方法都是私用，但它們出現在 IntelliSense 中。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 當您使用`StartCaching`方法，將資料物件加入至資料快取資料物件不需要以宣告<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性。 不過，資料物件必須符合特定需求，才能加入至資料快取。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。  
  
## <a name="to-programmatically-cache-a-data-object"></a>若要以程式設計方式快取資料物件  
  
1.  宣告類別層級，不是在方法內的資料物件。 這個範例假設您會宣告<xref:System.Data.DataSet>名為`dataSet1`您想要以程式設計方式快取。  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  具現化的資料物件，然後再呼叫`StartCaching`方法的文件或工作表的執行個體和傳入的資料物件的名稱。  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
## <a name="to-stop-caching-a-data-object"></a>若要停止快取資料物件  
  
1.  呼叫`StopCaching`方法的文件或工作表的執行個體和傳入的資料物件的名稱。 此範例假設您擁有<xref:System.Data.DataSet>名為`dataSet1`您想要停止快取。  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  請勿呼叫`StopCaching`從事件處理常式，如`Shutdown`文件或工作表的事件。 依時間`Shutdown`就會引發事件，就無法再修改的資料快取。 如需詳細資訊`Shutdown`事件，請參閱 < [Events in Office Projects](../vsto/events-in-office-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [快取資料](../vsto/caching-data.md)   
 [如何： 快取資料以供使用，離線或在伺服器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何： 快取受密碼保護的文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)   
 [將資料儲存](/visualstudio/data-tools/saving-data)  
  
  