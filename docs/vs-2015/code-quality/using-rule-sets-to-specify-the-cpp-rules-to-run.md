---
title: 使用規則集指定C++要執行規則 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e8361ec9f93ff150d3fd29bce315f635bd00048b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068635"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>使用規則集指定要執行的 C++ 規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]並[!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]，您可以建立和修改自訂*規則集*以符合程式碼分析與相關聯的特定專案需求。 若要建立自訂C++規則集，C /C++必須在 Visual Studio IDE 中開啟專案。 然後規則集編輯器中開啟的標準規則集，然後新增或移除特定規則及選擇性變更 [程式碼分析會判斷已違反規則時所發生的動作之後。  
  
 若要建立新的自訂規則集，您將使用新的檔案名稱儲存。 自訂規則集會自動指派至專案。  
  
## <a name="opening-the-rule-set-editor"></a>開啟規則集編輯器  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>若要從單一的現有規則集建立自訂規則  
  
1. 在 [方案總管] 中，開啟專案的捷徑功能表，然後再選擇**屬性**。  
  
2. 在 [**屬性**索引標籤上，選擇**程式碼分析**。  
  
3. 在 [**規則集**下拉式清單，請執行下列其中一項：  
  
   - 選擇您想要自訂的規則集。  
  
     \-或-  
  
   - 選擇 **\<瀏覽>** ，指定現有的規則集不在清單中。  
  
4. 選擇**開啟**至規則集編輯器中顯示的規則。  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要修改規則規則集編輯器中設定  
  
- 若要變更顯示名稱的規則集時，在**檢視**功能表上，選擇**屬性] 視窗**。 輸入中的顯示名稱**名稱**] 方塊中。 請注意，與檔案名稱，可以不同的顯示名稱。  
  
- 若要加入自訂規則集的所有規則的群組，請選取群組的核取方塊。 若要移除之群組的所有規則，請清除核取方塊。  
  
- 若要加入自訂規則集的特定規則，請選取規則的核取方塊。 若要移除的規則集的規則，請清除核取方塊。  
  
- 若要變更的程式碼分析中違反規則時所採取的動作，請選擇**動作**欄位規則，然後選擇 [下列值之一：  
  
     **警告**-會產生警告。  
  
     **錯誤**-會產生錯誤。  
  
     **無**-停用規則。 此動作會移除規則集合中的規則相同。  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>若要群組，篩選或變更規則集編輯器中的欄位使用規則集編輯器工具列  
  
- 若要展開所有群組中的規則，請選擇**全部展開**。  
  
- 若要摺疊所有群組中的規則，請選擇**全部摺疊**。  
  
- 若要變更規則依據該欄位，選擇 [從欄位**Group By**清單。 若要顯示未分組的規則，請選擇 **\<無>** 。  
  
- 若要新增或移除欄位規則的資料行中，選擇**資料行選項**。  
  
- 若要隱藏並不適用於目前的方案中的規則，請選擇**隱藏規則並不適用於目前的方案，**。  
  
- 若要顯示和隱藏指派錯誤動作的規則之間切換，請選擇**會顯示可以產生程式碼分析錯誤的規則**。  
  
- 若要顯示和隱藏指派 [警告] 動作的規則之間切換，請選擇**會顯示可以產生程式碼分析警告的規則**。  
  
- 若要切換顯示和隱藏規則指派**無**動作，選擇**會顯示未啟用的規則**。  
  
- 若要新增或移除的 Microsoft 預設規則將設定為目前的規則集，請選擇**新增或移除子規則集**。
