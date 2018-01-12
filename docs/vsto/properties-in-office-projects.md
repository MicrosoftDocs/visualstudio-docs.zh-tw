---
title: "Office 專案中的屬性 |Microsoft 文件"
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
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7925cc9b6988a79a855d6aa8d9cd91d1a4589559
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="properties-in-office-projects"></a>Office 專案中的屬性
  在 Visual Studio 中，Office 專案有幾個可用的重要屬性。 這些屬性可於 [屬性]  視窗中取得。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>主項目命名空間  
 使用**主項目命名空間**變更主項目類別的命名空間的屬性 (例如， `ThisAddIn`， `ThisWorkbook`，或`ThisDocument`類別) 在 Visual C# 專案中。 當您在 [方案總管]  中選取文件層級專案 (例如 ExcelWorkbook1.xlsx 或 WordDocument1.docx) 的文件節點，或 VSTO 增益集專案 (例如 Excel 或 Word) 的應用程式節點時，這個屬性會出現在 [屬性] 視窗中。  
  
 當您建立 Visual C# Office 專案時，主項目會根據專案名稱獲得命名空間。 建議您使用 [主項目命名空間]  屬性變更命名空間，不要直接編輯程式碼檔案。 當您使用這個屬性時，就會變更產生 (隱藏) 的程式碼檔案中的命名空間，可見的程式碼檔案也一樣。  
  
## <a name="cacheindocument"></a>CacheInDocument  
 當您在 Visual Studio Designer 中選取 **的執行個體時，[CacheInDocument]****屬性就會出現在文件層級專案的 [屬性]**<xref:System.Data.DataSet> 視窗中。 只能快取公用成員；如果想要快取 **，請確定 [Modifiers]****屬性設為 [Public]**<xref:System.Data.DataSet>。  
  
 這個屬性接受布林值：  
  
-   選取 **true** 快取文件中的資料集。  
  
-   選取 **false** ，如果您不要快取文件中的資料集。  
  
 如需快取資料的詳細資訊，請參閱 [Cached Data in Document-Level Customizations](../vsto/cached-data-in-document-level-customizations.md)。  
  
## <a name="value2"></a>Value2  
 [Value2]  屬性只適用於 Excel 活頁簿或範本專案。 當您選取工作表設計工具上的 **控制項時，它會出現在 [屬性]****視窗的 [Databindings]**<xref:Microsoft.Office.Tools.Excel.NamedRange> 屬性節點下。  
  
 使用 [屬性]  視窗的 [Value2]  屬性，將 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 屬性繫結至資料來源的欄位。  
  
## <a name="see-also"></a>請參閱  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)   
 [Office 專案中的事件](../vsto/events-in-office-projects.md)  
  
  