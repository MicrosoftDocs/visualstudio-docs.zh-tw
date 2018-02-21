---
title: "如何： 建立自訂規則集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3095d5eff59506f3d7681f61f11f73d37258647d
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-create-a-custom-rule-set"></a>如何：建立自訂規則集

在 Visual Studio 中，您可以建立和修改自訂*規則集*以符合與程式碼分析相關聯的特定專案需求。 建立自訂規則集、 開啟一個或多標準規則設定規則集編輯器中。 您可以再新增或移除特定規則，您可以變更程式碼分析會判斷已違反規則時所發生的動作。

 若要建立新的自訂規則集，您將使用新的檔案名稱儲存。 自訂規則集會自動指派至專案。

## <a name="opening-the-rule-set-editor"></a>開啟規則集編輯器

### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>若要開啟空白規則集檔案中規則集編輯器

1. 在**檔案**功能表[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，指向 **新增**，然後按一下 **檔案**。

2. 在**新檔案**對話方塊中，按一下 **一般**中**已安裝的範本**清單，然後再選取**程式碼分析規則集**。

3. 規則集編輯器隨即出現。 [編輯器] 清單中不選取任何規則。

### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>若要從單一的現有規則集建立自訂規則

1. 在方案總管 中，以滑鼠右鍵按一下專案，然後選取**屬性**。

2. 在**屬性**索引標籤上，按一下 **程式碼分析**。

3. 在**規則集**下拉式清單中，執行下列其中一項：

    - 選取您想要自訂的規則集。

     \-或-

    - 選取**\<瀏覽 >** ，指定現有的規則集不在清單中。

4. 按一下**開啟**至規則集編輯器中顯示的規則。

### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>從多個現有的規則集建立自訂規則集

1. 在方案總管 中，以滑鼠右鍵按一下專案，然後選取**屬性**。

2. 在**屬性**索引標籤上，按一下 **程式碼分析**。

3. 選取**\<選擇多個規則的設定...>**從**執行此規則集**。

4. 在**新增或移除規則集**對話方塊中，選取規則集您想要作為新的規則集，然後按一下 **確定**。

5. 儲存新的規則集。

     中已選取新的規則集的名稱**執行此規則集**清單。 您可以變更下一個步驟中的規則集的顯示名稱。

6. （選擇性）若要變更顯示名稱的規則集時，在**檢視**功能表上，按一下 [**屬性] 視窗**。 輸入中的顯示名稱**名稱**方塊。

7. 若要加入，移除，或修改新規則集中的特定程式碼分析規則，請按一下**開啟**。

## <a name="modifying-a-rule-set"></a>修改規則集

### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要修改規則規則集編輯器中設定

- 若要變更顯示名稱的規則集時，在**檢視**功能表上，按一下 [**屬性] 視窗**。 輸入中的顯示名稱**名稱**方塊。 請注意，顯示名稱可以不同的檔案名稱。

- 若要加入自訂規則集之群組的所有規則，請選取群組的核取方塊。 若要移除群組的所有規則，請清除核取方塊。

- 若要加入自訂規則集的特定規則，請選取規則的核取方塊。 若要移除規則規則集，清除核取方塊。

- 若要變更時違反規則的程式碼分析中採取的動作，請按一下中**動作**欄位規則，然後選取下列值之一：

     **警告**-會產生警告。

     **錯誤**-會產生錯誤。

     **無**-停用規則。 這個動作等同於從規則集移除規則。

## <a name="changing-the-rule-set-editor-display"></a>變更規則將編輯器的顯示設定

### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>若要分組，篩選或變更規則集編輯器中的欄位使用規則集編輯器工具列

- 若要展開所有群組中的規則，請按一下**全部展開**。

- 若要摺疊所有群組中的規則，請按一下**全部摺疊**。

- 若要變更規則會依分組的欄位，請選取 從欄位**Group By**清單。 若要顯示未分組的規則，請選取**\<無 >**。

- 若要加入或移除欄位規則的資料行中，按一下**資料行選項**。

- 若要隱藏的規則，不會套用到目前的方案，**隱藏不會套用至目前方案的規則**。

- 若要顯示和隱藏指派錯誤動作的規則之間切換，請按一下**顯示可以產生程式碼分析錯誤規則**。

- 若要顯示和隱藏指派警告動作的規則之間切換，請按一下**顯示可以產生程式碼分析警告的規則**。

- 若要切換顯示和隱藏規則指派**無**動作，按一下**顯示未啟用的規則**。

- 若要新增或移除的 Microsoft 預設規則設定為目前的規則集，請按一下**新增或移除子規則集**。

## <a name="see-also"></a>請參閱

[如何： 設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
[程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)