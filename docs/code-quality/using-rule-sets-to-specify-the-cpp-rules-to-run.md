---
title: 使用規則集指定要執行的 C++ 規則
ms.date: 04/28/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 061b52a683992bdc2fe5792ab05e00f788434a0f
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018217"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>使用規則集指定要執行C++的規則

在 Visual Studio 中，您可以建立和修改自訂*規則集*，以符合與程式碼分析相關聯的特定專案需求。 預設的規則集會儲存在 `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` 中。

**Visual Studio 2017 15.7 版和更新**版本您可以使用任何文字編輯器來建立自訂規則集，並將其套用在命令列組建中，不論您使用的組建系統為何。 如需詳細資訊，請參閱[/analyze：規則集](/cpp/build/reference/analyze-code-analysis)。

若要在 Visual Studio C++中建立自訂規則集，必須C++在 Visual Studio IDE 中開啟 C/專案。 接著，您可以在 [規則集編輯器] 中開啟標準規則集，然後新增或移除特定規則，並選擇性地變更程式碼分析判斷違反規則時所發生的動作。

若要建立新的自訂規則集，請使用新的檔案名加以儲存。 自訂規則集會自動指派給專案。

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>從單一現有規則集建立自訂規則

1. 在方案總管中，開啟專案的快捷方式功能表，然後選擇 [**屬性**]。

2. 在 [**屬性**] 索引標籤上，選擇 [程式**代碼分析**]。

3. 在 [**規則集**] 下拉式清單中，執行下列其中一項動作：

   - 選擇您想要自訂的規則集。

     \-或-

   - 選擇 [ **\<Browse >** ]，指定不在清單中的現有規則集。

4. 選擇 [**開啟**] 以顯示規則集編輯器中的規則。

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要在規則集編輯器中修改規則集

- 若要變更規則集的顯示名稱，請在 [ **View** ] 功能表上選擇 [**屬性視窗]** 。 在 [**名稱**] 方塊中輸入顯示名稱。 請注意，顯示名稱可能與檔案名不同。

- 若要將群組的所有規則新增至自訂規則集，請選取群組的核取方塊。 若要移除群組的所有規則，請清除此核取方塊。

- 若要將特定規則新增至自訂規則集，請選取規則的核取方塊。 若要從規則集移除規則，請清除此核取方塊。

- 若要變更程式碼分析中違反規則時所採取的動作，請選擇規則的 [**動作**] 欄位，然後選擇下列其中一個值：

     **警告**-產生警告。

     **錯誤**-產生錯誤。

     **無**-停用規則。 此動作與從規則集移除規則相同。

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>若要使用 [規則集編輯器] 工具列來分組、篩選或變更 [規則集編輯器] 中的欄位

- 若要展開所有群組中的規則，請選擇 [全部**展開**]。

- 若要折迭所有群組中的規則，**請選擇 [全部折**迭]。

- 若要變更規則分組依據的欄位，請從 [**分組方式**] 清單中選擇欄位。 若要顯示未分組的規則，請選擇 **\<無>** 。

- 若要在規則資料行中新增或移除欄位，請選擇 [**資料行選項**]。

- 若要隱藏不會套用至目前解決方案的規則，請選擇 [**隱藏不適用於目前解決方案的規則**]。

- 若要在顯示和隱藏已指派錯誤動作的規則之間進行切換，請選擇 [**顯示可以產生程式碼分析錯誤的規則**]。

- 若要在顯示和隱藏已指派警告動作的規則之間進行切換，請選擇 [**顯示可以產生程式碼分析警告的規則**]。

- 若要在顯示和隱藏已指派 [**無**] 動作的規則之間進行切換，請選擇 [**顯示未啟用的規則**]。

- 若要新增或移除目前規則集的 Microsoft 預設規則集，請選擇 [**新增或移除子規則集**]。

## <a name="to-create-a-rule-set-in-a-text-editor"></a>在文字編輯器中建立規則集

您可以在文字編輯器中建立自訂規則集，並將它儲存在任何具有 @no__t 0 擴充功能的位置，然後使用[/analyze：規則集](/cpp/build/reference/analyze-code-analysis)編譯器選項來套用。

下列範例顯示基本的規則集檔案，可供您做為起點：

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
