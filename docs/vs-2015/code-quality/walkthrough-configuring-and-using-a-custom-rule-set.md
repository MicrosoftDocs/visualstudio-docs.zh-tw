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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fa3a91df779094e3e11722dfc7bfc03c58bcea7e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383411"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>逐步解說：設定和使用自訂規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何使用已設定為使用自訂的程式碼分析工具*規則集*類別庫。 您可以選取與您指定您的解決方案，或者您可以選取的專案類型替代的規則集要滿足特定需求，例如掃描舊版程式碼可以在不中斷的方式中修正的問題相關的規則集。 在任一情況下，規則集也可以自訂來微調它們以您的專案需求。  
  
 在本逐步解說中，您會逐步執行這些程序：  
  
- 建立類別庫。  
  
- 選取  **Microsoft 基本設計方針規則**程式碼分析規則集。  
  
- 將您自己的程式碼新增至類別。  
  
- 執行程式碼分析。  
  
- 自訂規則集。  
  
- 執行程式碼分析，請參閱 < 設定自訂行為的運作方式的規則。  
  
## <a name="prerequisites"></a>必要條件  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]或 [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>使用規則集使用程式碼分析  
 首先，建立簡單的類別庫。  
  
#### <a name="create-a-class-library"></a>建立類別庫  
  
1. 在 [檔案]  功能表上，按一下 [新增]  及 [專案]  。  
  
2. 在 **新的專案**對話方塊的 **專案類型**，按一下  **Visual C#** 。  
  
3. 底下**Visual C#** ，選取**類別庫**。  
  
4. 在 **名稱**文字方塊中，輸入**RuleSetSample** ，然後按一下 **確定**。  
  
   接下來，您將在其中選取**Microsoft 基本設計方針規則**規則集，並將它儲存與您的專案。  
  
#### <a name="select-a-code-analysis-rule-set"></a>選取程式碼分析規則集  
  
1. 在 **分析**功能表上，按一下**RuleSetSample 設定程式碼分析**。  
  
    程式碼分析的組態設定會出現。  
  
2. 在 **執行此規則集**下拉式清單中，選取**Microsoft 所有規則**。  
  
    如需可用的規則集的詳細資訊，請參閱[程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)。  
  
    在 檔案 功能表中，按一下 **儲存選取項目**與您所選取規則集的相關資訊和其設定更新專案檔。  
  
   > [!TIP]
   > 在真實世界的情況下，最好使用排列優先順序的問題，您想要使用程式碼分析的目標是開始**最小建議規則**規則集和更正所需的問題，然後以累加方式新增更多的規則設定為找出並解決其他問題。  
  
   接下來，您會加入一些程式碼，到將用來示範違規 CA1704 的類別庫 」 的識別項應該使用正確的拼字"程式碼分析規則。 如需詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
#### <a name="add-your-own-code"></a>新增您自己的程式碼  
  
- 在 [方案總管] 中開啟 Class1.cs 檔案，並將現有的程式碼取代為下列：  
  
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
  
  現在您可以在 RuleSetSample 的專案執行程式碼分析，並尋找任何錯誤和錯誤清單 視窗中產生的警告。  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample 專案執行程式碼分析  
  
1. 在 **分析**功能表上，按一下**RuleSetSample 上執行程式碼分析**。  
  
2. 在 [錯誤清單] 視窗中，按一下**警告**，然後按一下**描述**欄標題來排序警告文數字順序。  
  
    在真實世界應用程式中，您會修正值得到目前為止，修正任何規則違規或選擇性地關閉或隱藏的規則，如果您決定不值得修正。 如需詳細資訊，請參閱[使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。  
  
3. 請注意 CA1704 警告。 這些在這項規則的違規會指出，您應該 「 考慮提供更有意義的名稱，參數。 」 您可以在程式碼中修正此問題，或在下一個程序中所述，您可以停用規則。  
  
   接下來，您將自訂規則集排除 CA1704 警告，「 識別項應該使用正確的拼字"。  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>自訂規則集的專案，以停用特定的規則  
  
1. 在 **分析**功能表上，按一下**RuleSetSample 設定程式碼分析**。  
  
2. 在 **執行此規則集**下拉式清單中，確認**Microsoft 所有規則**規則集仍然會反白顯示，然後按一下 **開啟**。 [規則集] 頁面會顯示。  
  
3. 展開 Microsoft.Naming 類別目錄 節點中，，然後選取 CA1704 警告。  
  
4. 底下**動作**欄中，選取**None。** 這可防止 CA1704 顯示為警告或錯誤清單 視窗中的錯誤。  
  
    現在會是試驗不同的工具列按鈕的好時機，並篩選選項，來熟悉它們。 例如，您可以使用**Group By**下拉式清單，協助找出特定的規則的類別。 另一個例子是，您可以使用**隱藏停用的規則**隱藏或顯示使用的所有規則規則集頁面工具列中的按鈕**動作**資料行設定為**None**。 這可以是很有用，如果您想要掃描以確認您仍想將它們停用已關閉的任何規則。  
  
5. 在 [檢視] 功能表中，按一下 [屬性] 視窗。 型別**My 自訂規則集**屬性 工具視窗的 名稱 方塊中。 這會變更新規則中設定的顯示名稱[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]IDE。  
  
6. 在上**檔案**功能表上，按一下**儲存 Microsoft 所有 Rules.ruleset**若要儲存您自訂的規則集合。 瀏覽至您的專案根資料夾。 在 **檔名**文字方塊中，輸入**MyCustomRuleSet**。 自訂規則集現在可以選取與您的專案搭配使用。  
  
   使用新的規則集建立，現在必須設定您的專案設定來指定您想要使用您新的規則集與它。  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>指定新的規則集，以便使用與您的專案  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按**屬性**。  
  
2. 在 **屬性**索引標籤上，按一下**程式碼分析**。  
  
    在 **執行此規則集**下拉式清單中，按一下 **\<瀏覽...>** 。 瀏覽至您的程式碼專案的根資料夾，然後選取 **MyCustomRuleSet.ruleset** 。 這是您在上一個程序中建立新規則集。  
  
3. 在上**檔案**功能表上，按一下**儲存**以儲存您的專案組態。 自訂規則集現在可以搭配您的專案。  
  
   最後，您將執行一次使用您 MyCustomRuleSet 規則集的程式碼分析。 請注意 [錯誤清單] 視窗不會顯示 CA1704 效能規則違規。  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>第二次 RuleSetSample 專案執行程式碼分析  
  
1. 在 **分析**功能表上，按一下**RuleSetSample 上執行程式碼分析**。  
  
2. 在 [錯誤清單] 視窗中，請注意，當您按一下**警告**，您不會再看見 CA1704 警告違規 」 的識別項應該使用正確的拼字"規則。  
  
## <a name="see-also"></a>另請參閱  
 [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)
