---
title: 建立自訂程式碼分析規則集
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a7ed11e7d3e093afaeaa19fd87ea68b7fecd266
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816561"
---
# <a name="customize-a-rule-set"></a>自訂規則集

您可以建立自訂規則集以符合特定專案需求的程式碼分析。

## <a name="create-a-custom-rule-set"></a>建立自訂規則集

若要建立自訂規則集，您可以開啟內建的規則中設定**規則集編輯器**。 從該處，您可以新增或移除特定規則，而且您可以變更時違反規則時所發生的動作&mdash;比方說，顯示警告或錯誤。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，然後選取**屬性**。

2. 在 [**屬性**頁面，選取**程式碼分析**] 索引標籤。

3. 在 **執行此規則集**下拉式清單，請執行下列其中一項：

   - 選取您想要自訂的規則集。

     \-或-

   - 選取 [ **\<瀏覽] >** ，指定現有的規則集不在清單中。

4. 選取 **開啟**至規則集編輯器中顯示的規則。

您也可以建立新的規則集檔案從**新的檔案**對話方塊：

1. 選取 **檔案** > **新增** > **檔案**，或按**Ctrl**+**N**.

2. 在**新的檔案**對話方塊中，選取**一般**左側的類別目錄，然後選取**程式碼分析規則集**。

3. 選取 [開啟] 。

   新 *.ruleset*規則集編輯器中開啟檔案。

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>建立自訂規則集從多個規則集

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按**屬性**。

2. 在 [**屬性**頁面，選取**程式碼分析**] 索引標籤。

3. 選取  **\<選擇多個規則集...>** 從**執行此規則集**。

4. 在 [**新增或移除規則集**] 對話方塊中，選取此規則會為您想要包含在新的規則集。

   ![新增或移除規則集對話方塊](media/add-remove-rule-sets.png)

5. 選取 **另存新檔**，輸入的名稱 *.ruleset*檔案，然後再選取**儲存**。

   中已選取新的規則集**執行此規則集**清單。

6. 選取 **開啟**開啟新的規則集編輯器中設定的規則。

### <a name="rule-precedence"></a>規則優先順序

- 如果相同的規則列出的兩個或更多時間在規則中設定不同的嚴重性，編譯器會產生錯誤。 例如：

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- 相同的規則是否列出的兩次或多次中設定的規則*同一*嚴重性，您可能會看到下列警告**錯誤清單**:

   **CA0063:無法載入規則集檔案 '\[您].ruleset' 或其中一個相依的規則集檔案。檔案不符合規則集的結構描述。**

- 如果規則集包含子規則集利用**Include**標籤和子系和父代規則集清單相同的規則，但不同的嚴重性，然後在父代規則集的嚴重性會優先。 例如: 

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>名稱和描述

若要變更在編輯器中開啟的規則集的顯示名稱，開啟**屬性**視窗中的選取**檢視** > **屬性 視窗**功能表列上。 輸入中的顯示名稱**名稱** 方塊中。 您也可以輸入規則集的描述。

## <a name="next-steps"></a>後續步驟

既然您已設定的規則下, 一個步驟是自訂的規則，藉由新增或移除規則，或修改規則違規的嚴重性。

> [!div class="nextstepaction"]
> [修改規則集編輯器中的規則](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>另請參閱

- [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)