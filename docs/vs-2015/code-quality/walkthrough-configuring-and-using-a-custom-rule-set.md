---
title: 逐步解說：設定和使用自訂規則集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645745"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>逐步解說：設定和使用自訂規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何使用已設定為在類別庫上使用自訂*規則集*的程式碼分析工具。 您可以選取與您為解決方案指定的專案類型相關的規則集，也可以選取替代的規則集來滿足特定需求，例如掃描舊版程式碼，找出可透過不中斷的方式修正的問題。 不論是哪一種情況，也可以自訂規則集，以微調您的專案需求。

 在本逐步解說中，您將逐步執行這些程式：

- 建立類別庫。

- 選取 [ **Microsoft 基本設計指導方針規則**程式碼分析規則集]。

- 將您自己的程式碼新增至類別。

- 執行程式碼分析。

- 自訂規則集。

- 執行程式碼分析，並查看規則集自訂行為的運作方式。

## <a name="prerequisites"></a>必要條件

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]或 [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>使用規則集搭配程式碼分析
 首先，建立一個簡單的類別庫。

#### <a name="create-a-class-library"></a>建立類別庫

1. 在 [檔案] 功能表上，按一下 [新增] 及 [專案]。

2. 在 [**新增專案**] 對話方塊的 [**專案類型**] 底下，按一下 [**視覺效果C#** ]。

3. 在 **[ C#視覺效果**] 底下，選取 [**類別庫**]。

4. 在 [**名稱**] 文字方塊中，輸入**RuleSetSample** ，然後按一下 **[確定]** 。

   接下來，您將選取**Microsoft 基本設計指導方針規則**規則集，並將它儲存在您的專案中。

#### <a name="select-a-code-analysis-rule-set"></a>選取程式碼分析規則集

1. 在 [**分析**] 功能表上，按一下 [**設定 RuleSetSample 的程式碼分析**]。

    [程式碼分析] 的設定會隨即出現。

2. 在 [**執行此規則集**] 下拉式清單中，選取 [ **Microsoft 所有規則**]。

    如需可用規則集的詳細資訊，請參閱程式[代碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)。

    在 [檔案] 功能表上，按一下 [**儲存選取的專案**] 以更新專案檔，其中包含您所選取之規則集的相關資訊及其設定。

   > [!TIP]
   > 在真實世界的情況下，使用來設定您想要以程式碼分析為目標的問題的最佳作法，就是從**最小的建議規則**規則集開始，然後更正所需的問題，再以累加方式將其他規則或規則集新增至尋找並更正其他問題。

   接下來，您會將一些程式碼新增至類別庫，以用來示範是否違反 CA1704 「識別碼應正確拼寫」程式碼分析規則。 如需詳細資訊，請參閱 [CA1704：識別碼應該正確拼寫 ](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

#### <a name="add-your-own-code"></a>新增您自己的程式碼

- 在方案總管中，開啟 Class1.cs 檔案，並將現有的程式碼取代為下列內容：

  ```
  using System;
  using System.Collections.Generic;
  using System.Text;

  namespace RuleSetSample
  {
      public class Class1
      {
          //The variable parameter names "a" and "b" will cause
          //the warning CA 1704 Microsoft.Naming "Consider
          //providing a more meaningful name" to fire
          public int AddIntegers(int a, int b)
          {

              int sum = a + b;

              return (sum);
          }
      }
  }

  ```

  現在您可以在 RuleSetSample 專案上執行程式碼分析，並尋找在錯誤清單視窗中產生的任何錯誤和警告。

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>在 RuleSetSample 專案上執行程式碼分析

1. 在 [**分析**] 功能表上，按一下 [**在 RuleSetSample 上執行程式碼分析**]。

2. 在 [錯誤清單] 視窗中，按一下 [**警告**]，然後按一下 [**描述**] 欄標題，以排序警告排序。

    在真實世界的應用程式中，您會在此時修正目前值得修正的任何規則違規，或選擇性地關閉或隱藏規則（如果您確定不值得修正）。 如需詳細資訊，請參閱[使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。

3. 請注意 CA1704 警告。 對於此規則的違規，表示您應該考慮為參數提供更有意義的名稱。」 您可以更正程式碼中的問題，或停用規則，如下一個程式所述。

   接下來，您將自訂規則集以排除 CA1704 警告「識別碼應正確拼寫」。

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>自訂專案的規則集以停用特定規則

1. 在 [**分析**] 功能表上，按一下 [**設定 RuleSetSample 的程式碼分析**]。

2. 在 [**執行此規則集**] 下拉式清單中，確認 [ **Microsoft 所有規則**] 規則集仍已反白顯示，然後按一下 [**開啟**]。 [規則集] 頁面隨即顯示。

3. 展開 [Microsoft 命名類別目錄] 節點，然後選取 [CA1704] 警告。

4. 在 [**動作**] 資料行底下，選取 [**無]。** 這可防止 CA1704 在錯誤清單視窗中顯示為警告或錯誤。

    現在可以開始體驗各種工具列按鈕和篩選選項，以熟悉它們。 例如，您可以使用 [**分組方式**] 下拉式清單來協助尋找特定規則或規則類別。 另一個範例是，您可以使用 [規則集頁面] 工具列中的 [**隱藏停用的規則**] 按鈕，隱藏或顯示 [**動作**] 資料行設為 [**無**] 的所有規則。 如果您想要掃描已關閉的任何規則，以確認您是否仍要將其停用，這會很有用。

5. 在 [檢視] 功能表上，按一下 [屬性視窗]。 在 [屬性] 工具視窗的 [名稱] 方塊中，輸入**我的自訂規則集**。 這會變更 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE 中新規則集的顯示名稱。

6. **在 [檔案**] 功能表上，按一下 [**儲存 Microsoft 所有規則]。規則**集，以儲存您的自訂規則集。 流覽至專案的根資料夾。 在 **[檔案名**] 文字方塊中，輸入**MyCustomRuleSet**。 現在可以選取自訂規則集，以用於您的專案。

   建立新的規則集之後，您現在必須設定專案設定，以指定您想要搭配使用新的規則集。

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>指定要與您的專案搭配使用的新規則集

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選取 [**屬性**]。

2. 在 [**屬性**] 索引標籤中，按一下 [程式**代碼分析**]。

    在 [**執行此規則集**] 下拉式清單中，按一下 [\<Browse]。 **>** 。 流覽至程式碼專案的根資料夾，然後選取 [ **MyCustomRuleSet**]。 這是您在上一個程式中建立的新規則集。

3. **在 [檔案**] 功能表上，按一下 [**儲存**] 來儲存您的專案設定。 自訂規則集現在可以與您的專案搭配使用。

   最後，您將使用 MyCustomRuleSet 規則集再次執行程式碼分析。 請注意，[錯誤清單] 視窗不會顯示 CA1704 效能規則違規。

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>第二次在 RuleSetSample 專案上執行程式碼分析

1. 在 [**分析**] 功能表上，按一下 [**在 RuleSetSample 上執行程式碼分析**]。

2. 在 [錯誤清單] 視窗中，請注意，當您按一下 [**警告**] 時，就不會再看到「識別碼應該正確拼寫」規則的 CA1704 警告違規。

## <a name="see-also"></a>另請參閱
 [如何：為 Managed 程式碼專案設定程式碼分析 ](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) 程式[代碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)
