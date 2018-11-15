---
title: 如何： 建立自訂規則集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a5d8a5cb7e29cfd900ce81fa5f4b6253f0c49014
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812461"
---
# <a name="how-to-create-a-custom-rule-set"></a>如何：建立自訂規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在  [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]， [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]，並[!INCLUDE[vsPro](../includes/vspro-md.md)]，您可以建立和修改自訂*規則集*以符合程式碼分析與相關聯的特定專案需求。 若要建立自訂規則集、 開啟一個或更標準的規則集規則集編輯器中。 您接著可以新增或移除特定規則，您可以變更程式碼分析會判斷已違反規則時所發生的動作。  
  
 若要建立新的自訂規則集，您將使用新的檔案名稱儲存。 自訂規則集會自動指派至專案。  
  
## <a name="opening-the-rule-set-editor"></a>開啟規則集編輯器  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>若要開啟空白規則，請設定規則集編輯器中的檔案  
  
1.  在 **檔案**功能表[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]，指向**新增**，然後按一下 **檔案**。  
  
2.  在 [**新的檔案**] 對話方塊中，按一下**一般**中**已安裝的範本**清單，然後再選取**程式碼分析規則集**。  
  
3.  規則集編輯器隨即出現。 在 [編輯器] 清單中未不選取任何規則。  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>若要從單一的現有規則集建立自訂規則  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按**屬性**。  
  
2. 在 **屬性**索引標籤上，按一下**程式碼分析**。  
  
3. 在 **規則集**下拉式清單，請執行下列其中一項：  
  
   - 選取您想要自訂的規則集。  
  
     \-或-  
  
   - 選取 [ **\<瀏覽] >** ，指定現有的規則集不在清單中。  
  
4. 按一下 **開啟**至規則集編輯器中顯示的規則。  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>要建立自訂規則集，從多個現有的規則集  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按**屬性**。  
  
2.  在 **屬性**索引標籤上，按一下**程式碼分析**。  
  
3.  選取  **\<選擇多個規則集...>** 從**執行此規則集**。  
  
4.  在 **新增或移除規則集**對話方塊中，選取規則集您想要作為新的規則集，然後按一下**確定**。  
  
5.  儲存新的規則集。  
  
     在 選取新的規則集的名稱**執行此規則集**清單。 您可以變更下一個步驟中的規則集的顯示名稱。  
  
6.  （選擇性）若要變更顯示名稱的規則集時，在**檢視**功能表上，按一下**屬性 視窗**。 輸入中的顯示名稱**名稱** 方塊中。  
  
7.  若要加入，移除，或修改新的規則集內的特定程式碼分析規則，請按一下**開啟**。  
  
## <a name="modifying-a-rule-set"></a>修改規則集  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要修改規則規則集編輯器中設定  
  
-   若要變更顯示名稱的規則集時，在**檢視**功能表上，按一下**屬性 視窗**。 輸入中的顯示名稱**名稱** 方塊中。 請注意，與檔案名稱，可以不同的顯示名稱。  
  
-   若要加入自訂規則集的所有規則的群組，請選取群組的核取方塊。 若要移除之群組的所有規則，請清除核取方塊。  
  
-   若要加入自訂規則集的特定規則，請選取規則的核取方塊。 若要移除的規則集的規則，請清除核取方塊。  
  
-   若要變更的程式碼分析中違反規則時所採取的動作，請按一下**動作**欄位規則，然後選取下列值之一：  
  
     **警告**-會產生警告。  
  
     **錯誤**-會產生錯誤。  
  
     **無**-停用規則。 此動作會移除規則集合中的規則相同。  
  
## <a name="changing-the-rule-set-editor-display"></a>變更規則集編輯器顯示  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>若要群組，篩選或變更規則集編輯器中的欄位使用規則集編輯器工具列  
  
-   若要展開所有群組中的規則，請按一下**全部展開**。  
  
-   若要摺疊所有群組中的規則，請按一下**全部摺疊**。  
  
-   若要變更規則依據該欄位，選取 從欄位**Group By**清單。 若要顯示未分組的規則，請選取**\<無 >**。  
  
-   若要新增或移除欄位規則的資料行中，按一下**資料行選項**。  
  
-   若要隱藏，不會套用至目前方案中，規則**隱藏規則並不適用於目前的方案，**。  
  
-   若要顯示和隱藏指派錯誤動作的規則之間切換，請按一下**會顯示可以產生程式碼分析錯誤的規則**。  
  
-   若要顯示和隱藏指派 [警告] 動作的規則之間切換，請按一下**會顯示可以產生程式碼分析警告的規則**。  
  
-   若要切換顯示和隱藏規則指派**無**動作，按一下**會顯示未啟用的規則**。  
  
-   若要新增或移除的 Microsoft 預設規則將設定為目前的規則集，請按一下**新增或移除子規則集**。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)



