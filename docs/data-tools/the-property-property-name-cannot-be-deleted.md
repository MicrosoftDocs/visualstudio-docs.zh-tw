---
title: "屬性&lt;屬性名稱&gt;無法刪除 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b3a896e64e048a5104bca84b726c730d4d9d524a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>屬性&lt;屬性名稱&gt;無法刪除
屬性\<屬性名稱 > 無法刪除，因為它會設定為**鑑別子屬性**間之繼承\<類別名稱 > 和\<類別名稱 >  
  
 選取的屬性設定為**鑑別子屬性**錯誤訊息中所指出的類別之間的繼承。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。  
  
 設定**鑑別子屬性**不同的屬性，為資料類別，以啟用成功刪除的所需的屬性。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  在 O/R Designer 中，選取在錯誤訊息指出的資料類別之間連接的繼承關聯線。  
  
2.  設定**鑑別子**的不同屬性的屬性。  
  
3.  試著再次刪除屬性。  
  
## <a name="see-also"></a>請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)