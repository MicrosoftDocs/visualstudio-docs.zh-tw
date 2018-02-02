---
title: "逐步解說： 設定及使用自訂規則集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b9a7046930d12ebb940820eb25c4563b0a3213e3
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>逐步解說：設定和使用自訂規則集

本逐步解說示範如何使用已設定為使用自訂的程式碼分析工具*規則集*類別庫。 您可以選取規則集相關的專案類型，您可以選取或指定您的解決方案，替代的規則集來滿足特定需求，例如掃描舊版程式碼中斷的方式，可以修正的問題。 在任一情況下，規則集也可以自訂來微調他們自己專案的需求。  
  
在本逐步解說中，您將逐步執行這些程序：  
  
-   建立類別庫。  
  
-   選取**Microsoft 基本設計方針規則**程式碼分析規則集。  
  
-   將您自己的程式碼加入至類別。  
  
-   執行程式碼分析。  
  
-   自訂規則集。  
  
-   執行程式碼分析，請參閱如何在規則中設定自訂表現方式。  
  
## <a name="using-rule-sets-with-code-analysis"></a>使用規則集的程式碼分析

首先，建立簡單類別庫。  
  
### <a name="create-a-class-library"></a>建立類別庫  
  
1.  在 [檔案]  功能表上，按一下 [新增]  及 [專案] 。  
  
2.  在**新專案**對話方塊的 **專案類型**，按一下  **Visual C#**。  
  
3.  在下**Visual C#**，選取**類別庫**。  
  
4.  在**名稱**文字方塊中，輸入**RuleSetSample** ，然後按一下 **確定**。  
  
 接下來，您會選取**Microsoft 基本設計方針規則**規則集，並將它儲存您的專案。  
  
### <a name="select-a-code-analysis-rule-set"></a>選取程式碼分析規則集  
  
1.  上**分析**功能表上，按一下 **設定程式碼分析 RuleSetSample**。  
  
     程式碼分析的組態設定會出現。  
  
2.  在**執行此規則集**下拉式清單中，選取**Microsoft 所有規則**。  
  
     如需可用的規則集的詳細資訊，請參閱[程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)。  
  
     在 [檔案] 功能表上按一下**儲存選取項目**與您選取的規則集的相關資訊和其設定更新專案檔。  
  
    > [!TIP]
    >  在真實世界的情況下，最好的作法是用於設定優先權的問題，您想要使用程式碼分析的目標是，開始**最小建議規則**規則集和所需的問題，然後再以累加方式加入更多的規則設定為找出並解決其他問題。  
  
 接下來，您會加入一些程式碼，到將用來示範違規的 CA1704 類別庫 」 的識別項應該使用正確的拼字 」 程式碼分析規則。 如需詳細資訊，請參閱[CA1704： 識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
### <a name="add-your-own-code"></a>加入您自己的程式碼  
  
-   在 [方案總管] 中開啟 Class1.cs 檔並以下列內容取代現有的程式碼：  
  
    ```csharp
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
  
現在您可以 RuleSetSample 專案執行程式碼分析，並尋找任何錯誤和錯誤清單 視窗中產生的警告。  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample 專案執行程式碼分析  
  
1.  在**分析**功能表上，按一下  **RuleSetSample 上執行程式碼分析**。  
  
2.  在 錯誤清單 視窗中，按一下 **警告**，然後按一下 **描述**行標頭以便排序警告文數字順序。  
  
     在真實世界應用程式中，您修正值得此時，修正任何規則違規或選擇性地關閉或隱藏的規則，如果您決定不需要處理。 如需詳細資訊，請參閱[使用 SuppressMessage 屬性所隱藏的警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。  
  
3.  請注意 CA1704 警告。 這些違規這個規則表示，您應該 「 請考慮提供更有意義的名稱，參數。 」 您無法更正問題，您的程式碼中或下一個程序中所述，您可以停用規則。  
  
 接下來，您將自訂的規則集排除 CA1704 警告、 」 識別項應該使用正確的拼字"。  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>自訂規則集的專案，以停用特定的規則  
  
1.  上**分析**功能表上，按一下 **設定程式碼分析 RuleSetSample**。  
  
2.  在**執行此規則集**下拉式清單中，確認**Microsoft 所有規則**規則集仍會反白顯示，然後按一下 **開啟**。 規則設定頁面會顯示。  
  
3.  展開 Microsoft.Naming 類別目錄節點，然後選取 CA1704 警告。  
  
4.  在下**動作**欄中，選取**None。** 這可防止 CA1704 顯示為警告或錯誤清單 視窗中的錯誤。  
  
     現在是試驗不同的工具列按鈕的好時機和篩選選項，以熟悉使用。 例如，您可以使用**Group By**下拉式清單，協助找出特定的規則的類別。 另一個例子是，您可以使用**隱藏停用的規則**來隱藏或顯示的所有規則規則集頁面工具列中的按鈕**動作**資料行設為**無**。 這很有用，如果您想要掃描以確認您仍然想要將它們停用已關閉的任何規則。  
  
5.  在 [檢視] 功能表中，按一下 [屬性] 視窗。 型別**我自訂規則集**屬性的 [工具] 視窗的 [名稱] 方塊中。 這會變更新規則中設定的顯示名稱[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]IDE。  
  
6.  在**檔案**功能表上，按一下 **儲存 Microsoft 所有 Rules.ruleset**儲存您的自訂的規則集。 瀏覽至您的專案的根資料夾。 在**FileName**文字方塊中，輸入**MyCustomRuleSet**。 自訂規則集現在可以選取用於您的專案。  
  
使用建立新規則集，現在需要設定您的專案設定來指定您想要使用您設定它的新規則。  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>指定新的規則集，以便使用您的專案  
  
1.  在方案總管 中，以滑鼠右鍵按一下專案，然後選取**屬性**。  
  
2.  在**屬性**索引標籤上，按一下 **程式碼分析**。  
  
     在**執行此規則集**下拉式清單中，按一下  **\<瀏覽...>**。 瀏覽至您的程式碼專案的根資料夾，然後選取**MyCustomRuleSet.ruleset**。 這是您在上一個程序中建立新規則集。  
  
3.  在**檔案**功能表上，按一下 **儲存**儲存您的專案組態。 自訂規則集現在可以搭配您的專案。  
  
 最後，您將執行一次使用 MyCustomRuleSet 規則集的程式碼分析。 請注意，[錯誤清單] 視窗不會顯示 CA1704 效能規則違規。  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>第二次 RuleSetSample 專案執行程式碼分析  
  
1.  在**分析**功能表上，按一下  **RuleSetSample 上執行程式碼分析**。  
  
2.  在 [錯誤清單] 視窗中，請注意，當您按一下**警告**，您不會再看見 CA1704 警告違規 」 的識別項應該使用正確的拼字 」 規則。  
  
## <a name="see-also"></a>另請參閱

[如何： 設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)