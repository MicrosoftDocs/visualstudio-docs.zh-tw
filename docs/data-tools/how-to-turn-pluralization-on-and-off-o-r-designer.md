---
title: 'How to: Turn pluralization on and off (O-R Designer) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 6f0fe07b55ae0eeb57c0cc11fed047f31966cb6e
ms.openlocfilehash: 6d920152eedc41e307fcba6dcf0d56cf9cf367d9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>How to: Turn pluralization on and off (O/R Designer)
By default, when you drag database objects that have names ending in s or ies from **Server Explorer**/**Database Explorer** onto the [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), the names of the generated entity classes are changed from plural to singular. This is done to more accurately represent the fact that the instantiated entity class maps to a single record of data. For example, adding a Customers table to the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] results in an entity class named Customer because the class will hold data for only a single customer.  
  
> [!NOTE]
>  Pluralization is on by default only in the English-language version of Visual Studio.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>To turn pluralization on and off  
  
1.  On the **Tools** menu, click **Options**.  
  
2.  In the **Options** dialog box, expand **Database Tools**.  
  
> [!NOTE]
>  Select **Show all settings** if the **Database Tools** node is not visible.  
  
1.  Click **O/R Designer**.  
  
2.  Set **Pluralization of names** to **Enabled** = **False** to set the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] so that it does not change class names.  
  
3.  Set **Pluralization of names** to **Enabled** = **True** to apply pluralization rules to the class names of objects added to the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="see-also"></a>See Also  
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Accessing data in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
