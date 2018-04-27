---
title: 使用規則集指定要執行的 C++ 規則
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ccb64fba6a646de0974c9de6e35beb98738b7300
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>使用指定要執行的 c + + 規則規則集

在 Visual Studio 中，您可以建立和修改自訂*規則集*以符合與程式碼分析相關聯的特定專案需求。 預設的規則集儲存在`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`。

**Visual Studio 2017 版本 15.7**您可以建立自訂規則集使用任何文字編輯器，並將它們套用在命令列組建，不論您使用的系統建立什麼。 如需詳細資訊，請參閱[/analyze: ruleset](/cpp/build/reference/analyze-code-quality)。

若要建立自訂的 c + + 規則，在 Visual Studio 中設定，必須在 Visual Studio IDE 中開啟 C/c + + 專案。 您再規則集編輯器中開啟標準規則集然後加入或移除特定規則，以及選擇性地變更程式碼分析會判斷已違反規則時所發生的動作。

若要建立新的自訂規則集，您將使用新的檔案名稱儲存。 自訂規則集會自動指派至專案。

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>若要從單一的現有規則集建立自訂規則

1. 在 方案總管 中，開啟專案的捷徑功能表，然後選擇 **屬性**。

2. 在**屬性**索引標籤上，選擇**程式碼分析**。

3. 在**規則集**下拉式清單中，執行下列其中一項：

    - 選擇您想要自訂的規則集。

     \-或-

    - 選擇**\<瀏覽 >** ，指定現有的規則集不在清單中。

4. 選擇**開啟**至規則集編輯器中顯示的規則。

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要修改規則規則集編輯器中設定

- 若要變更顯示名稱的規則集時，在**檢視**功能表上，選擇**屬性 視窗**。 輸入中的顯示名稱**名稱**方塊。 請注意，顯示名稱可以不同的檔案名稱。

- 若要加入自訂規則集之群組的所有規則，請選取群組的核取方塊。 若要移除群組的所有規則，請清除核取方塊。

- 若要加入自訂規則集的特定規則，請選取規則的核取方塊。 若要移除規則規則集，清除核取方塊。

- 若要變更時違反規則的程式碼分析中採取的動作，請選擇**動作**欄位規則，然後選擇下列值之一：

     **警告**-會產生警告。

     **錯誤**-會產生錯誤。

     **無**-停用規則。 這個動作等同於從規則集移除規則。

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>若要分組，篩選或變更規則集編輯器中的欄位使用規則集編輯器工具列

- 若要展開所有群組中的規則，請選擇**全部展開**。

- 若要摺疊所有群組中的規則，請選擇**全部摺疊**。

- 若要變更該規則會依分組的欄位，選擇 從欄位**Group By**清單。 若要顯示未分組的規則，請選擇**\<無 >**。

- 若要加入或移除欄位規則的資料行中，選擇 **資料行選項**。

- 若要隱藏的規則，不會套用到目前的方案，請選擇**隱藏不會套用至目前方案的規則**。

- 若要顯示和隱藏指派錯誤動作的規則之間切換，請選擇**顯示可以產生程式碼分析錯誤規則**。

- 若要顯示和隱藏指派警告動作的規則之間切換，請選擇**顯示可以產生程式碼分析警告的規則**。

- 若要切換顯示和隱藏規則指派**無**動作，選擇**顯示未啟用的規則**。

- 若要新增或移除的 Microsoft 預設規則設定為目前的規則集，請選擇**新增或移除子規則集**。

## <a name="to-create-a-rule-set-in-a-text-editor"></a>若要建立規則，在文字編輯器中設定

您可以建立自訂規則集的文字編輯器、 將它儲存在任何位置`.ruleset`延伸模組，並套用在與[/analyze: ruleset](/cpp/build/reference/analyze-code-quality)編譯器選項。

下列範例示範基本的規則集檔案，您可以使用做為起點：

```xml

<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```
