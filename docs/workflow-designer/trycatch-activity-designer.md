---
title: TryCatch 活動設計工具 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ae4cd4340bc30249ea649a2806afe3e027fc439
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="trycatch-activity-designer"></a>TryCatch 活動設計工具
**TryCatch**活動設計工具用來建立及設定<xref:System.Activities.Statements.TryCatch>活動。

## <a name="the-trycatch-activity"></a>TryCatch 活動
 <xref:System.Activities.Statements.TryCatch>活動包含<xref:System.Activities.Statements.TryCatch.Try%2A>活動，集合**攔截\<TException >**和<xref:System.Activities.Statements.TryCatch.Finally%2A>活動。 A<xref:System.Activities.Statements.Catch%601>型別的**TException**包含<xref:System.Activities.Statements.Catch%601.ExceptionType%2A>和<xref:System.Activities.Statements.Catch%601.Action%2A>。 它們會共同用來實作一般例外狀況式錯誤處理機制。 <xref:System.Activities.Statements.TryCatch> 活動會嘗試執行其 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動。 如果<xref:System.Activities.Statements.TryCatch.Try%2A>活動會擲回任何例外狀況，<xref:System.Activities.Statements.TryCatch>活動會使用其**攔截 < TException\>** 集合以符合例外狀況。 如果沒有相符項目，然後在<xref:System.Activities.Statements.Catch%601.Action%2A>對應**攔截\<TException >**執行時，做為錯誤處理邏輯的例外狀況。 如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中的活動順利完成，或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中的活動順利完成，則 <xref:System.Activities.Statements.TryCatch> 活動會執行它的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動。 如需詳細資訊，請參閱[Windows 工作流程例外狀況](/dotnet/framework/windows-workflow-foundation/exceptions)。

### <a name="using-the-trycatch-activity-designer"></a>使用 TryCatch 活動設計工具
 **TryCatch**活動設計工具位於**錯誤處理**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左半部[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTLR + ALT + X。)

 **TryCatch**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.TryCatch> 活動，具有 TryCatch 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**TryCatch**活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在介面上編輯**TryCatch**活動設計工具。

 按一下右上角的展開按鈕**TryCatch**設計工具，請參閱**再試一次**，**攔截**，和**最後**中展開的檢視。 若要加入 catch，請按一下**新增快取**按鈕**TryCatch**設計工具。 按鈕會變更為型別下拉式方塊。 請選取例外狀況型別，並按 ENTER 鍵來加入 Catch。 在新增之後**攔截**catch 區域會展開，可以將活動置放於 catch 以定義 catch 的執行邏輯。 請注意，展開的 Catch 區域右側有一個文字方塊 您可以使用這個文字方塊來命名例外狀況變數。 例外狀況變數僅能在相同的活動**攔截**。

 **TryCatch**設計工具不支援編輯**攔截**。 如果您想要變更的例外狀況類型，您必須刪除**攔截**並加入新的。 A**攔截**可以藉由選取並刪除它或使用刪除**刪除**上以滑鼠右鍵按一下 [內容] 功能表的功能表。

### <a name="the-trycatch-properties"></a>TryCatch 屬性
 下表顯示<xref:System.Activities.Statements.TryCatch>屬性並描述設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.TryCatch> 活動選用的易記名稱。 預設為 TryCatch。|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|當 <xref:System.Activities.Statements.TryCatch> 執行時，首先執行的活動。|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|集合**攔截**時，要檢查的項目<xref:System.Activities.Statements.TryCatch.Try%2A>活動會擲回的例外狀況。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|當 <xref:System.Activities.Statements.TryCatch.Try%2A> 和 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中的任何必要活動完成執行時，要執行的活動。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [重新擲回](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)