---
title: 屬性&lt;屬性名稱&gt;無法刪除 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b065500c9c881a7190b59c4d70a0433eb8864c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186520"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>屬性&lt;屬性名稱&gt;無法刪除
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
屬性\<屬性名稱 > 不能刪除，因為它設定為間之繼承鑑別子屬性\<類別名稱 > 和\<類別名稱 >  
  
 選取的屬性設定為**鑑別子屬性**類別間之繼承所示的錯誤訊息。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。  
  
 設定**鑑別子屬性**不同的屬性，可以成功刪除要刪的屬性資料類別。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  在 O/R Designer 中，選取在錯誤訊息指出的資料類別之間連接的繼承關聯線。  
  
2.  設定**鑑別子**的不同屬性的屬性。  
  
3.  試著再次刪除屬性。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [資料類別繼承 （O/R 設計工具）](../data-tools/data-class-inheritance-o-r-designer.md)   
 [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

