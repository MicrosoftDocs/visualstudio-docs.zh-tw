---
title: How to：建立自訂規則集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657454"
---
# <a name="how-to-create-a-custom-rule-set"></a>如何：建立自訂規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]、[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 和 [!INCLUDE[vsPro](../includes/vspro-md.md)] 中，您可以建立和修改自訂*規則集*，以符合與程式碼分析相關聯的特定專案需求。 若要建立自訂規則集，請在 [規則集編輯器] 中開啟一或多個標準規則集。 接著，您可以新增或移除特定規則，也可以變更程式碼分析判斷違反規則時所發生的動作。

 若要建立新的自訂規則集，請使用新的檔案名加以儲存。 自訂規則集會自動指派給專案。

## <a name="opening-the-rule-set-editor"></a>開啟規則集編輯器

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>若要在規則集編輯器中開啟空白的規則集檔案

1. **在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 的 [檔案**] 功能表上，指向 [**新增**]，**然後按一下 [** 檔案]。

2. 在 [**新增**檔案] 對話方塊中，按一下 [**已安裝的範本**] 清單中的 **[一般**]，然後選取 [程式**代碼分析規則集**]。

3. [規則集編輯器] 隨即出現。 在 [編輯器] 清單中未選取任何規則。

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>從單一現有規則集建立自訂規則

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選取 [**屬性**]。

2. 在 [**屬性**] 索引標籤上，按一下 [程式**代碼分析**]。

3. 在 [**規則集**] 下拉式清單中，執行下列其中一項動作：

   - 選取您要自訂的規則集。

     \-或-

   - 選取 **\<Browse .。。>** ，指定不在清單中的現有規則集。

4. 按一下 [**開啟**]，以在 [規則集編輯器] 中顯示規則。

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>若要從多個現有的規則集建立自訂規則集

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選取 [**屬性**]。

2. 在 [**屬性**] 索引標籤上，按一下 [程式**代碼分析**]。

3. 選取 **\<Choose 多個規則集 .。。** 從**執行此規則集**>。

4. 在 [新增**或移除規則集**] 對話方塊中，選取您要做為新規則集基礎的規則集，然後按一下 **[確定]** 。

5. 儲存新的規則集。

     新規則集的名稱會在 [**執行此規則集**] 清單中選取。 您可以在下一個步驟中變更規則集的顯示名稱。

6. 選擇性若要變更規則集的顯示名稱，請在 [ **View** ] 功能表上，按一下 [**屬性視窗]** 。 在 [**名稱**] 方塊中輸入顯示名稱。

7. 若要新增、移除或修改新規則集中的特定程式碼分析規則，請按一下 [**開啟**]。

## <a name="modifying-a-rule-set"></a>修改規則集

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要在規則集編輯器中修改規則集

- 若要變更規則集的顯示名稱，請在 [ **View** ] 功能表上，按一下 [**屬性視窗]** 。 在 [**名稱**] 方塊中輸入顯示名稱。 請注意，顯示名稱可能與檔案名不同。

- 若要將群組的所有規則新增至自訂規則集，請選取群組的核取方塊。 若要移除群組的所有規則，請清除此核取方塊。

- 若要將特定規則新增至自訂規則集，請選取規則的核取方塊。 若要從規則集移除規則，請清除此核取方塊。

- 若要變更程式碼分析中違反規則時所採取的動作，請在規則的 [**動作**] 欄位中按一下，然後選取下列其中一個值：

     **警告**-產生警告。

     **錯誤**-產生錯誤。

     **無**-停用規則。 此動作與從規則集移除規則相同。

## <a name="changing-the-rule-set-editor-display"></a>變更規則集編輯器顯示

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>若要使用 [規則集編輯器] 工具列來分組、篩選或變更 [規則集編輯器] 中的欄位

- 若要展開 [所有群組] 中的規則，請按一下 [全部**展開**]。

- 若要折迭所有群組中的規則，請按一下 [**全部**折迭]。

- 若要變更規則分組依據的欄位，請從 [**群組依據**] 清單中選取欄位。 若要顯示未分組的規則，請選取 [ **\<None >** ]。

- 若要在規則資料行中新增或移除欄位，請按一下 [**資料行選項**]。

- 若要隱藏不適用於目前方案的規則，請隱藏不會套用**至目前解決方案的規則**。

- 若要在顯示和隱藏已指派錯誤動作的規則之間進行切換，請按一下 [**顯示可能會產生程式碼分析錯誤的規則**]。

- 若要在顯示和隱藏已指派警告動作的規則之間進行切換，請按一下 [**顯示可以產生程式碼分析警告的規則**]。

- 若要在顯示和隱藏已指派 [**無**] 動作的規則之間進行切換，請按一下 [**顯示未啟用的規則**]。

- 若要新增或移除目前規則集的 Microsoft 預設規則集，請按一下 [**新增或移除子規則集**]。

## <a name="see-also"></a>請參閱
 [如何：為 Managed 程式碼專案設定程式碼分析的程式](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)代碼[分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)
