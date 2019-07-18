---
title: 您有來自不受支援的資料庫提供者選取資料庫物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d2812e316d17c347341e97ec9594162a2252e4d0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688225"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) For SQL Server 支援.NET Framework 資料提供者 (<xref:System.Data.SqlClient>)。 雖然您可以按一下 [確定] 繼續使用來自不支援之資料庫提供者的物件，但是在執行階段可能會發生非預期性行為。  
  
> [!NOTE]
> 只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 按一下 [確定] 以繼續設計對應到使用不受支援之資料庫提供者之連線的實體類別。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。  
  
     -或-  
  
- 按一下 [取消]。  
  
     會停止動作。 請建立或使用 .NET Framework Provider for SQL Server 提供的資料連接。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [.NET Framework 資料提供者](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   