---
title: 您有來自不受支援的資料庫提供者選取資料庫物件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8e051a5533f02946e9e28a08abd4c4a1326aca8f
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879295"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio 2017 文件](/visualstudio/)。  
  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) For SQL Server 支援.NET Framework 資料提供者 (<xref:System.Data.SqlClient>)。 雖然您可以按一下**確定**並繼續使用不支援的資料庫提供者的物件，您可能會在執行階段遇到非預期的行為。  
  
> [!NOTE]
>  只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   按一下 **確定**繼續設計實體類別對應至使用不支援的資料庫提供者的連接。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。  
  
     -或-  
  
-   按一下 **取消**。  
  
     會停止動作。 請建立或使用 .NET Framework Provider for SQL Server 提供的資料連接。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [.NET framework 資料提供者](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)

