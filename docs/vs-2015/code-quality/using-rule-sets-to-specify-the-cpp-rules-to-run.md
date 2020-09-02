---
title: 使用規則集指定要執行的 c + + 規則 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277861"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>使用規則集指定要執行的 C++ 規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 和中 [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] ，您可以建立和修改自訂 *規則集* ，以符合與程式碼分析相關聯的特定專案需求。 若要建立自訂 c + + 規則集，必須在 Visual Studio IDE 中開啟 C/c + + 專案。 然後，您可以在規則集編輯器中開啟標準規則集，然後新增或移除特定規則，並選擇性地變更程式碼分析判斷違反規則時所發生的動作。  
  
 若要建立新的自訂規則集，請使用新的檔案名進行儲存。 自訂規則集會自動指派給專案。  
  
## <a name="opening-the-rule-set-editor"></a>開啟規則集編輯器  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>從單一現有的規則集建立自訂規則  
  
1. 在方案總管中，開啟專案的快捷方式功能表，然後選擇 [ **屬性**]。  
  
2. 在 [ **屬性** ] 索引標籤上，選擇 [程式 **代碼分析**]。  
  
3. 在 [ **規則集** ] 下拉式清單中，執行下列其中一項：  
  
   - 選擇您要自訂的規則集。  
  
     \- 或 -  
  
   - 選擇 **\<Browse...>** 指定不在清單中的現有規則集。  
  
4. 選擇 [ **開啟** ]，在規則集編輯器中顯示規則。  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要在規則集編輯器中修改規則集  
  
- 若要變更規則集的顯示名稱，請在 [ **View** ] 功能表上選擇 [ **屬性視窗]**。 在 [ **名稱** ] 方塊中輸入顯示名稱。 請注意，顯示名稱可能與檔案名不同。  
  
- 若要將群組的所有規則新增至自訂規則集，請選取群組的核取方塊。 若要移除群組的所有規則，請清除該核取方塊。  
  
- 若要將特定規則新增至自訂規則集，請選取規則的核取方塊。 若要從規則集中移除規則，請清除該核取方塊。  
  
- 若要變更程式碼分析違反規則時所採取的動作，請選擇規則的 [ **動作** ] 欄位，然後選擇下列其中一個值：  
  
     **警告** -會產生警告。  
  
     **錯誤** -產生錯誤。  
  
     **無** -停用規則。 此動作與從規則集移除規則相同。  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>使用規則集編輯器工具列來群組、篩選或變更規則集編輯器中的欄位  
  
- 若要展開所有群組中的規則，請選擇 [ **全部展開**]。  
  
- 若要折迭所有群組中的規則，請選擇 [ **全部**折迭]。  
  
- 若要變更規則分組依據的欄位，請從 [ **群組依據** ] 清單中選擇欄位。 若要顯示已取消分組的規則，請選擇 **\<None>** 。  
  
- 若要在規則資料行中新增或移除欄位，請選擇 [ **資料行選項**]。  
  
- 若要隱藏未套用至目前方案的規則，請選擇 [隱藏未套用 **至目前解決方案的規則**]。  
  
- 若要在顯示和隱藏指派錯誤動作的規則之間切換，請選擇 [ **顯示可產生程式碼分析錯誤的規則**]。  
  
- 若要在顯示和隱藏指派警告動作的規則之間切換，請選擇 [ **顯示可產生程式碼分析警告的規則**]。  
  
- 若要在顯示和隱藏指派 [ **無** ] 動作的規則之間切換，請選擇 [ **顯示未啟用的規則**]。  
  
- 若要新增或移除目前規則集的 Microsoft 預設規則集，請選擇 [ **新增或移除子規則集**]。
