---
title: 如何： 使用 O-R 設計工具設定繼承 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ccfbd40fd9fd62921ff6f0661f87dca2995ae8fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496428"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>如何： 使用 O/R 設計工具設定繼承
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 使用 O-R 設計工具設定繼承](https://docs.microsoft.com/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)。  
  
  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) 通常是在關聯式系統中實作，因此支援單一資料表繼承概念。 在單一資料表繼承 (Inheritance) 中，單一資料庫資料表的欄位會同時包含父代資訊和子系資料。 使用關聯式資料時，鑑別子資料行所含的值會決定任何記錄所屬的類別 (Class)。  
  
 例如，假設有個 Persons 資料表包含某家公司雇用的所有人員。 有些人是員工，而有些人是經理。 這個 Persons 資料表包含一個名為 `EmployeeType` 的資料行 (其中值 1 代表經理，值 2 代表員工)，這就是鑑別子資料行。 在這個案例中，您可以建立員工子類別 (Subclass)，並且只將 `EmployeeType` 值為 2 的記錄填入 (Populate) 這個類別。 您也可以從每個類別中移除不適用的資料行。  
  
 建立使用繼承的物件模型 (並對應至關聯式資料) 在過程上較為複雜。 下列程序將會說明使用 O/R 設計工具設定繼承的必要步驟。 因為在不參考現有資料表和資料行的情況下遵循這些泛型步驟，將是一件困難的事，所以提供了使用資料的逐步解說。 針對使用設定繼承的詳細逐步指示[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，請參閱 <<c2> [ 逐步解說： 建立的 LINQ to SQL 類別，以使用單一資料表繼承 （O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)。  
  
### <a name="to-create-inherited-data-classes"></a>若要建立繼承的資料類別  
  
1.  開啟[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]加上**LINQ to SQL 類別**至現有的 Visual Basic 或 C# 專案的項目。  
  
2.  將想要當成基底類別 (Base Class) 的資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。  
  
3.  拖曳資料表拖曳至第二份[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]並將它重新命名。 這就是衍生類別 (Derived Class) 或子類別。  
  
4.  按一下 **繼承**中**物件關聯式設計工具**索引標籤**工具箱**，然後按一下 子類別 （已重新命名的資料表），並將它連接到基底類別。  
  
    > [!NOTE]
    >  按一下 **繼承**中的項目**工具箱**並放開滑鼠按鈕、 按一下您在步驟 3 中，建立類別的第二個副本，然後按一下 您在步驟 2 中建立的第一個類別。 繼承線的箭號會指向第一個類別。  
  
5.  在每個類別中，刪除任何不想要顯示而且沒有用於關聯的物件屬性。 如果您嘗試刪除用於關聯的物件屬性，您會收到錯誤：[屬性\<的屬性名稱 > 不能刪除，因為它正參與關聯\<關聯名稱 >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  因為衍生類別會繼承其基底類別中定義的屬性，所以這兩個類別中不可以定義相同的資料行  (資料行是以屬性形式實作)。在基底類別的屬性上設定 [繼承修飾詞]，就可以啟用衍生類別中的資料行建立作業。 如需詳細資訊，請參閱 <<c0> [ 不在組建中： 覆寫屬性和方法](http://msdn.microsoft.com/en-us/2167e8f5-1225-4b13-9ebd-02591ba90213)。  
  
6.  選取 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中的繼承線。  
  
7.  在 **屬性**視窗中，將**鑑別子屬性**用來區分您的類別中的資料錄的資料行名稱。  
  
8.  設定**衍生類別鑑別子值**屬性設為將記錄指定為繼承的型別之資料庫中的值。 (這是儲存在鑑別子資料行中，用於指定繼承類別的值)。  
  
9. 設定**基底類別鑑別子值**屬性設為將記錄指定為基底類型的值。 (這是儲存在鑑別子資料行中，用於指定基底類別的值)。  
  
10. （選擇性） 您也可以設定**繼承預設值**屬性，以指定的型別繼承階層架構時載入的資料列不符合任何已定義繼承碼使用。 換句話說，如果記錄的鑑別子資料行中的值不符合中的值**衍生類別鑑別子值**或是**基底類別鑑別子值**屬性，記錄會載入到指定為的型別**繼承預設值**。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [逐步解說： 建立 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [PAVE 適用於 Visual Studio 2012 中的資料應用程式開發最新消息](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [逐步解說： 建立 LINQ to SQL 類別使用單一資料表繼承 （O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/en-us/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [繼承](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

