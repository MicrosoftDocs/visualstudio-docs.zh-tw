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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26bb37d1ddeabb77b1399c6cbce5ae55b59702c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654666"
---
# <a name="trycatch-activity-designer"></a>TryCatch 活動設計工具
[ **TryCatch** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.TryCatch> 活動。

## <a name="the-trycatch-activity"></a>TryCatch 活動
 @No__t_0 活動包含 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動、 **Catch \<TException**的集合 > 和 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動。 **TException**類型的 <xref:System.Activities.Statements.Catch%601> 包含 <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> 和 <xref:System.Activities.Statements.Catch%601.Action%2A>。 它們會共同用來實作一般例外狀況式錯誤處理機制。 <xref:System.Activities.Statements.TryCatch> 活動會嘗試執行其 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動。 如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動擲回任何例外狀況，則 <xref:System.Activities.Statements.TryCatch> 活動會使用其**Catch < TException \>** 集合來符合例外狀況。 如果相符，則會執行對應**Catch \<TException >** 的 <xref:System.Activities.Statements.Catch%601.Action%2A>，做為例外狀況的錯誤處理邏輯。 如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中的活動順利完成，或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中的活動順利完成，則 <xref:System.Activities.Statements.TryCatch> 活動會執行它的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][例外](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136)狀況。

### <a name="using-the-trycatch-activity-designer"></a>使用 TryCatch 活動設計工具
 [ **TryCatch** ] 活動設計**工具**位於 [工具箱] 的 [**錯誤處理**] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 左側的 [**工具箱**] 索引標籤（也可以選取 [ **工具列]，從[View** ] 功能表，或 CTLR + ALT + X）。

 [ **TryCatch** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立一個 <xref:System.Activities.Statements.TryCatch> 活動，具有 TryCatch 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 您可以在 [ **TryCatch** ] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。 其他屬性必須在 [ **TryCatch** ] 活動設計工具的介面上編輯。

 按一下 [ **TryCatch** ] 設計工具右上角的展開按鈕，以在展開的視圖中查看 [ **Try** **]、[** catch] 和 [ **Finally** ] 方塊。 若要加入 catch，請按一下 [ **TryCatch** ] 設計工具上的 [**加入新的 catch** ] 按鈕。 按鈕會變更為型別下拉式方塊。 請選取例外狀況型別，並按 ENTER 鍵來加入 Catch。 加入**catch**之後，catch 區域會展開，而且可以將活動拖放到 catch 中，以定義 catch 的執行邏輯。 請注意，展開的 Catch 區域右側有一個文字方塊 您可以使用這個文字方塊來命名例外狀況變數。 例外狀況變數只能用於相同**Catch**中的活動。

 **TryCatch**設計工具不支援編輯**Catch**。 如果您想要變更例外狀況類型，您必須刪除**Catch**並新增一個。 藉由選取**Catch**並加以刪除，或使用按一下滑鼠右鍵所存取之內容功能表上的 [**刪除**] 功能表，即可加以刪除。

### <a name="the-trycatch-properties"></a>TryCatch 屬性
 下表顯示 <xref:System.Activities.Statements.TryCatch>properties，並說明如何在設計工具中使用它們。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.TryCatch> 活動選用的易記名稱。 預設為 TryCatch。|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|當 <xref:System.Activities.Statements.TryCatch> 執行時，首先執行的活動。|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|@No__t_1 活動擲回例外狀況時，要檢查的**Catch**元素集合。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|當 <xref:System.Activities.Statements.TryCatch.Try%2A> 和 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中的任何必要活動完成執行時，要執行的活動。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|

## <a name="see-also"></a>請參閱
 [集合](../workflow-designer/collection-activity-designers.md)重新[引發](../workflow-designer/rethrow-activity-designer.md)[擲](../workflow-designer/throw-activity-designer.md)回