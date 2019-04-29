---
title: TryCatch 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e9d8c539d91c95b03f4946e256de7a825a6df7ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976604"
---
# <a name="trycatch-activity-designer"></a>TryCatch 活動設計工具
**TryCatch**活動設計工具會用來建立及設定<xref:System.Activities.Statements.TryCatch>活動。  
  
## <a name="the-trycatch-activity"></a>TryCatch 活動  
 <xref:System.Activities.Statements.TryCatch>活動包含<xref:System.Activities.Statements.TryCatch.Try%2A>活動，集合**攔截\<TException >** 和<xref:System.Activities.Statements.TryCatch.Finally%2A>活動。 A<xref:System.Activities.Statements.Catch%601>型別的**TException**包含<xref:System.Activities.Statements.Catch%601.ExceptionType%2A>和<xref:System.Activities.Statements.Catch%601.Action%2A>。 它們會共同用來實作一般例外狀況式錯誤處理機制。 <xref:System.Activities.Statements.TryCatch> 活動會嘗試執行其 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動。 如果<xref:System.Activities.Statements.TryCatch.Try%2A>活動會擲回任何例外狀況<xref:System.Activities.Statements.TryCatch>活動會使用其**攔截 < TException\>** 集合以符合例外狀況。 如果沒有相符項目，則<xref:System.Activities.Statements.Catch%601.Action%2A>對應**攔截\<TException >** 執行時，做為錯誤處理邏輯的例外狀況。 如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中的活動順利完成，或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中的活動順利完成，則 <xref:System.Activities.Statements.TryCatch> 活動會執行它的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][例外狀況](http://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136)。  
  
### <a name="using-the-trycatch-activity-designer"></a>使用 TryCatch 活動設計工具  
 **TryCatch**活動設計工具可在**錯誤處理**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左側[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTLR + ALT + X。)  
  
 **TryCatch**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.TryCatch> 活動，具有 TryCatch 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**TryCatch**活動設計工具或**DisplayName**屬性方格的方塊。 其他屬性必須的介面上編輯**TryCatch**活動設計工具。  
  
 按一下右上角的展開按鈕**TryCatch**設計工具，請參閱**嘗試**，**攔截**，以及**最後**中展開的檢視。 若要加入 catch，按一下**Přidat novou aktivitu catch**按鈕**TryCatch**設計工具。 按鈕會變更為型別下拉式方塊。 請選取例外狀況型別，並按 ENTER 鍵來加入 Catch。 在新增之後**攔截**catch 區域會展開，可以將活動置放於 catch 以定義 catch 的執行邏輯。 請注意，展開的 Catch 區域右側有一個文字方塊 您可以使用這個文字方塊來命名例外狀況變數。 例外狀況變數僅能在相同的活動**攔截**。  
  
 **TryCatch**設計工具不支援編輯**攔截**。 如果您想要變更的例外狀況類型，您必須刪除**攔截**並加入新的。 A**攔截**可以在選取它，然後刪除它，或使用刪除**刪除**功能表以滑鼠右鍵按一下，即可存取操作功能表上的。  
  
### <a name="the-trycatch-properties"></a>TryCatch 屬性  
 下表顯示<xref:System.Activities.Statements.TryCatch>內容並描述在設計工具的使用方式。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.TryCatch> 活動選用的易記名稱。 預設為 TryCatch。|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|當 <xref:System.Activities.Statements.TryCatch> 執行時，首先執行的活動。|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|集合**攔截**時，要檢查的項目<xref:System.Activities.Statements.TryCatch.Try%2A>活動會擲回的例外狀況。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|當 <xref:System.Activities.Statements.TryCatch.Try%2A> 和 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中的任何必要活動完成執行時，要執行的活動。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|  
  
## <a name="see-also"></a>另請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [重新擲回](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)