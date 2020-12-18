---
title: 建立自訂程式碼分析規則集
ms.date: 11/02/2018
description: 瞭解如何在 Visual Studio 中自訂程式碼分析規則集。 瞭解如何從頭開始建立新的集合，或從現有的集合建立新的集合。 瞭解規則優先順序。
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69af1534740ddec2c804f0b7dafec61d985a4b24
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97667880"
---
# <a name="customize-a-rule-set"></a>自訂規則集

您可以建立自訂規則集，以符合程式碼分析的特定專案需求。

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>從現有的規則集建立自訂規則集

若要建立自訂規則集，您可以在 [ **規則集編輯器**] 中開啟內建的規則集。 從該處，您可以新增或移除特定規則，也可以變更違反規則時所發生的動作 &mdash; ，例如顯示警告或錯誤。

1. 在 **方案總管** 中，以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。

2. 在 [ **屬性** ] 頁面上，選取 [程式 **代碼分析** ] 索引標籤。

::: moniker range="vs-2017"

3. 在 [ **執行此規則集** ] 下拉式清單中，執行下列其中一項：

::: moniker-end

::: moniker range=">=vs-2019"

3. 在 [作用中 **規則** ] 下拉式清單中，執行下列其中一項：

::: moniker-end

   - 選擇您要自訂的規則集。

     \- 或 -

   - 選取 **\<Browse>** 此項可指定不在清單中的現有規則集。

4. 選取 [ **開啟** ]，即可在規則集編輯器中顯示規則。

> [!NOTE]
> 如果您有 .NET Core 或 .NET Standard 專案，此程式會有些不同，因為專案屬性中的 [程式 **代碼分析** ] 索引標籤不支援相同的選項。 遵循下列步驟，將 [預先定義的規則集複製到您的專案，並將其設定為使用中的規則集](/dotnet/fundamentals/code-analysis/code-quality-rule-options)。 複製規則集之後，您可以 [在 Visual Studio 規則集編輯器中加以編輯](working-in-the-code-analysis-rule-set-editor.md) ，方法是從 **方案總管** 中開啟它。

## <a name="create-a-new-rule-set"></a>建立新的規則集

您可以從 [ **新增** 檔案] 對話方塊建立新的規則集檔案：

1. 選取 **[** 檔案新增檔案]  >    >  ****，或按 **Ctrl** + **N**。

2. 在 [ **新增** 檔案] 對話方塊中，選取左側的 **[一般** ] 類別，然後選取 [程式 **代碼分析規則集**]。

3. 選取 [開啟]。

   新的 *. 規則* 集檔案會在規則集編輯器中開啟。

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>從多個規則集建立自訂規則集

> [!NOTE]
> 下列程式不適用於 .NET Core 或 .NET Standard 專案，其在 [程式 **代碼分析** ] 屬性索引標籤中不支援相同的功能。

1. 在 **方案總管** 中，以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。

2. 在 [ **屬性** ] 頁面上，選取 [程式 **代碼分析** ] 索引標籤。

::: moniker range="vs-2017"

3. 選取 **\<Choose multiple rule sets>** [ **執行此規則集**]。

::: moniker-end

::: moniker range=">=vs-2019"

3. **\<Choose multiple rule sets>** 從作用中 **規則** 中選取。

::: moniker-end

4. 在 [新增 **或移除規則集** ] 對話方塊中，選擇您要包含在新規則集中的規則集。

   ![新增或移除規則集對話方塊](media/add-remove-rule-sets.png)

5. 選取 [ **另存** 新檔]，輸入 *規則集* 檔案的名稱，然後選取 [ **儲存**]。

   在 [ **執行此規則集** ] 清單中選取了新的規則集。

6. 選取 [ **開啟** ]，在規則集編輯器中開啟新的規則集。

## <a name="rule-precedence"></a>規則優先順序

- 如果相同的規則在具有不同嚴重性的規則集中列出兩次以上，則編譯器會產生錯誤。 例如：

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- 如果相同的規則在具有 *相同* 嚴重性的規則集中列出兩次以上，您可能會在 [ **錯誤清單**] 中看到下列警告：

   **CA0063：無法載入規則集檔案 ' 您的 ' \[ . 規則集 ' 或其相依的規則集檔案之一。檔案不符合規則集架構。**

- 如果規則集包含使用 **Include** 標記的子規則集，且子系和父規則設定都列出相同的規則，但有不同的嚴重性，則會優先使用父規則集的嚴重性。 例如：

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

若要變更在編輯器中開啟之規則集的顯示名稱，請選取功能表列上的 [**視圖**  >  **屬性視窗]** 來開啟 [屬性] 視窗。 在 [ **名稱** ] 方塊中輸入顯示名稱。 您也可以輸入規則集的描述。

## <a name="next-steps"></a>後續步驟

現在您已有規則集，下一步是藉由新增或移除規則，或修改規則違規的嚴重性來自訂規則。

> [!div class="nextstepaction"]
> [修改規則集編輯器中的規則](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>另請參閱

- [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)