---
title: Office 專案中的屬性
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fc2a0774206eac0c9295a425d81555ffdd3cac8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561357"
---
# <a name="properties-in-office-projects"></a>Office 專案中的屬性
  在 Visual Studio 中，Office 專案有幾個可用的重要屬性。 這些屬性可於 [屬性]  視窗中取得。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>主項目命名空間
 使用**主項目命名空間**屬性來變更主項目類別的命名空間 (例如`ThisAddIn`， `ThisWorkbook`，或`ThisDocument`類別) 視覺效果中C#專案。 此屬性會出現在**屬性**視窗中的文件層級專案，選取 [文件] 節點時 (例如*ExcelWorkbook1.xlsx*或是*WordDocument1.docx*) 或 VSTO 增益集專案 （例如 Excel 或 Word） 中的應用程式節點**方案總管 中**。

 當您建立 Visual C# Office 專案時，主項目會根據專案名稱獲得命名空間。 建議您使用 [主項目命名空間]  屬性變更命名空間，不要直接編輯程式碼檔案。 當您使用這個屬性時，就會變更產生 (隱藏) 的程式碼檔案中的命名空間，可見的程式碼檔案也一樣。

## <a name="cacheindocument"></a>CacheInDocument
 當您在 Visual Studio Designer 中選取 **的執行個體時，[CacheInDocument]屬性就會出現在文件層級專案的 [屬性]**<xref:System.Data.DataSet> 視窗中。 只能快取公用成員；如果想要快取 ，請確定 **[Modifiers]** 屬性設為 **[Public]**<xref:System.Data.DataSet>。

 這個屬性接受布林值：

- 選取 **true** 快取文件中的資料集。

- 選取 **false** ，如果您不要快取文件中的資料集。

  如需有關快取資料的詳細資訊，請參閱 [快取文件層級自訂中的資料](../vsto/cached-data-in-document-level-customizations.md)。

## <a name="value2"></a>Value2
 [Value2]  屬性只適用於 Excel 活頁簿或範本專案。 當您選取工作表設計工具上的 **控制項時，它會出現在 [屬性]** **視窗的 [Databindings]**<xref:Microsoft.Office.Tools.Excel.NamedRange> 屬性節點下。

 使用 [屬性]  視窗的 [Value2]  屬性，將 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 屬性繫結至資料來源的欄位。

## <a name="see-also"></a>另請參閱
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Office 專案範本概觀](../vsto/office-project-templates-overview.md)
- [Office 專案中的事件](../vsto/events-in-office-projects.md)
