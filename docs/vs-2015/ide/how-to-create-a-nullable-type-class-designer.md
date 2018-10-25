---
title: 如何：建立可為 Null 的類型 (類別設計工具) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab5bfe3068f79bceb02352b47de4beb08da75c85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941941"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>如何：建立可為 Null 的類型 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

特定實值型別不一定具有 (或需要) 定義的值。 這種情況在資料庫中為常見做法，其中的部分欄位不會指派任何值。 比方說，您可能將 null 值指派給資料庫欄位，以表示該欄位尚未指派值。  
  
 「可為 Null 的型別」是一種延伸的實值型別，其可接受該類型的一般範圍值，也可接受 null 值。 例如，您可將 -2147483648 到 2147483647 的任何值或 null 值指派給可為 Null 的 `Int32` (亦表示為Nullable\<Int32>)。 您可將 `True`、`False` 或 null 值 (完全沒有值) 指派給 Nullable\<bool>。  
  
 可為 Null 的型別是 <xref:System.Nullable%601> 結構的執行個體。 每個可為 Null 的型別，其執行個體皆有 `HasValue` 和 `Value` 這兩個公用唯讀屬性：  
  
- `HasValue` 是 `bool` 類型，並指出變數是否包含定義的值。 `True` 表示變數包含非 null 值。 您可以使用 `if (x.HasValue)` 或 `if (y != null)` 這類陳述式來測試是否有定義的值。  
  
- `Value` 是與基礎類型相同的類型。 如果 `HasValue` 為 `True`，則 `Value` 包含有意義的值。 如果 `HasValue` 為 `False`，則存取 `Value` 時會擲回無效作業例外狀況。  
  
  當您將變數宣告為可為 Null 的型別時，該變數預設為除了基礎實值型別的預設值之外，不具有任何已定義的值 (`HasValue` 為 `False`)。  
  
  [類別設計工具] 針對可為 Null 型別的顯示方式，完全與顯示其基礎類型一樣。  
  
  如需 Visual C# 可為 Null 型別的詳細資訊，請參閱[可為 Null 的型別](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)。 如需 Visual Basic 可為 Null 型別的詳細資訊，請參閱[可為 Null 的實值類型](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)。  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>若要使用類別設計工具，新增可為 Null 的型別  
  
1.  在類別圖表中，展開現有類別，或建立新的類別。  
  
2.  若要將類別新增至專案，請依序按一下 [類別圖表] 功能表上的 [新增] 和 [新增類別]。  
  
3.  若要展開類別圖形，請按一下 [類別圖表] 功能表上的 [展開]。  
  
4.  選取類別圖形。 在 [類別圖表] 功能表上，按一下 [新增]，然後按一下 [欄位]。 接著，在類別圖形和 [類別細節] 視窗中，即會出現一個新欄位 (預設名稱為 [欄位])。  
  
5.  在 [類別細節] 視窗 (或類別圖形本身) 的 [名稱] 資料行中，將新欄位的名稱變更為有效且有意義的名稱。  
  
6.  在 [類別細節] 視窗的 [類型] 資料行中，將類型宣告為可為 Null 的型別，如下列程式碼所示：  
  
    ```csharp  
    // Declare a nullable type in Visual C#:  
    class Test  
    {  
       int? building_number = 5;  
    }  
    ```  
  
    ```vb  
    ' Declare a nullable type in Visual Basic:  
    Class Test  
       Dim buildingNumber As Nullable(Of Integer) = 5  
    End Class  
    ```  
  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>若要使用程式碼編輯器，新增可為 Null 的型別  
  
1.  將類別加入至專案。 在方案總管中，選取專案節點，然後按一下 [專案] 功能表上的 [新增類別]。  
  
2.  若為新類別，可在 .cs 或 .vb 檔案中，將新類別中的一或多個可為 Null 的型別新增至類別宣告。  
  
3.  從 [類別檢視] 中，將新類別圖示拖曳至 [類別設計工具] 的設計介面。 類別圖表中隨即出現類別圖形。  
  
4.  展開類別圖形的詳細資料，然後將滑鼠指標移至類別成員上方。 工具提示會顯示每個成員的宣告。  
  
5.  以滑鼠右鍵按一下類別圖形，然後按一下 [類別細節]。 您可以在 [類別細節] 視窗中檢視或修改新類型的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Nullable%601>   
 [可為 Null 的型別](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)   
 [使用可為 Null 的型別](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)   
 [如何：識別可為 Null 的型別](http://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387)   
 [可為 Null 的值類型](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)



