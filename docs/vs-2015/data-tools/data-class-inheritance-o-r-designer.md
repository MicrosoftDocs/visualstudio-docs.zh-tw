---
title: 資料類別繼承 （O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2c1f5328abd8ea814e1175b17129dd8a89040ef
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697940"
---
# <a name="data-class-inheritance-or-designer"></a>資料類別繼承 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別就像其他物件，可以使用繼承，也可以衍生自其他類別。 在程式碼中，您可以宣告某個類別是繼承自其他類別，指定物件之間的繼承關聯性。 在資料庫中，有數種方式可以建立繼承關聯性。 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) 通常是在關聯式系統中實作，因此支援單一資料表繼承概念。  
  
 在單一資料表繼承中，有一種單一資料庫資料表，它包含了基底和衍生類別的資料行。 使用關聯式資料時，鑑別子資料行所含的值會決定某筆記錄所屬的類別 (Class)。 例如，假設有個 Persons 資料表包含某家公司雇用的所有人員。 有些人是員工，而有些人是經理。 這個 Persons 資料表包含名為 Type 的資料行 (其中值為 1 代表經理，值為 2 代表員工)。 Type 資料行就是鑑別子資料行。 在這個案例中，您可以建立員工子類別 (Subclass)，並且只將 Type 值為 2 的記錄填入 (Populate) 這個類別。  
  
 當您使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 在實體類別中設定繼承時，請將包含繼承資料的單一資料表拖曳至設計工具兩次：繼承階層中的每個類別各一次。 將資料表新增至設計工具之後，請使用 [物件關聯式設計工具] 工具箱的 [繼承] 項目連接這些資料表，然後在 [屬性] 視窗中設定四個繼承屬性。  
  
## <a name="inheritance-properties"></a>繼承屬性  
 下表列出繼承屬性及其描述：  
  
|屬性|描述|  
|--------------|-----------------|  
|鑑別子屬性|這個屬性 (對應至資料行) 會判斷目前記錄所屬的類別。|  
|基底類別鑑別子值|這個值 (在指定為鑑別子屬性的資料行中) 會判斷記錄是否為基底類別。|  
|衍生類別鑑別子值|這個值 (在指定為鑑別子屬性的屬性中) 會判斷記錄是否為衍生類別。|  
|繼承預設值|當屬性中的值指定為應填入的類別**鑑別子屬性**不符合**基底類別鑑別子值**或**衍生的類別鑑別子值**。|  
  
 建立使用繼承並對應至關聯式資料的物件模型在過程上較為複雜。 本主題提供設定繼承時，所需之基本概念和個別屬性的相關資訊。 下列主題則對於如何使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]設定繼承，提供了更清楚的說明。  
  
|主題|描述|  
|-----------|-----------------|  
|[如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|說明如何透過 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，設定使用單一資料表繼承的實體類別。|  
|[逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|提供逐步指示，說明如何透過 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，設定使用單一資料表繼承的實體類別。|  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [逐步解說：建立 LINQ to SQL 類別 （O-R 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [逐步解說：使用單一資料表繼承 （O/R 設計工具） 中建立 LINQ to SQL 類別](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [快速入門](https://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)
