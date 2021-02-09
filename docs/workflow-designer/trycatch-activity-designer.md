---
title: 工作流程設計工具 TryCatch 活動設計工具
description: 瞭解 TryCatch 活動，以及如何使用 TryCatch 活動設計工具來建立和設定 TryCatch 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23d9f1b0037600c6612a413cce7b089f6adbc7aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889300"
---
# <a name="trycatch-activity-designer"></a>TryCatch 活動設計工具

**TryCatch** 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.TryCatch> 活動。

## <a name="the-trycatch-activity"></a>TryCatch 活動
 <xref:System.Activities.Statements.TryCatch>活動包含 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動、 **Catch \<TException>** 和活動的集合 <xref:System.Activities.Statements.TryCatch.Finally%2A> 。 <xref:System.Activities.Statements.Catch%601> **TException** 類型的會包含 <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> 和 <xref:System.Activities.Statements.Catch%601.Action%2A> 。 它們會共同用來實作一般例外狀況式錯誤處理機制。 <xref:System.Activities.Statements.TryCatch> 活動會嘗試執行其 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動。 如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動擲回任何例外狀況，則 <xref:System.Activities.Statements.TryCatch> 活動會使用其 **Catch \><TException** 集合來符合例外狀況。 如果有相符的，則 <xref:System.Activities.Statements.Catch%601.Action%2A> 會執行對應 **Catch \<TException>** 的，做為例外狀況的錯誤處理邏輯。 如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中的活動順利完成，或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中的活動順利完成，則 <xref:System.Activities.Statements.TryCatch> 活動會執行它的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動。 如需詳細資訊，請參閱 [Windows workflow 例外](/dotnet/framework/windows-workflow-foundation/exceptions)狀況。

### <a name="using-the-trycatch-activity-designer"></a>使用 TryCatch 活動設計工具

存取 [工具箱] 的 [**錯誤處理**] 類別中的 [ **TryCatch** ] 活動設計 **工具**。

[ **TryCatch** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.TryCatch> 活動，具有 TryCatch 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以在 [ **TryCatch** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。 其他屬性必須在 [ **TryCatch** ] 活動設計工具的介面上進行編輯。

按一下 **TryCatch** 表設計工具右上角的展開按鈕，以查看展開視圖中的 [ **Try** **]、[** catch] 和 [ **Finally** ] 方塊。 若要加入 catch，請按一下 **TryCatch** 表設計工具上的 [**加入新的 catch** ] 按鈕。 按鈕會變更為型別下拉式方塊。 請選取例外狀況型別，並按 ENTER 鍵來加入 Catch。 加入 **catch** 之後，catch 區域會展開，而且可以將活動拖放到 catch 中，以定義 catch 的執行邏輯。 請注意，展開的 Catch 區域右側有一個文字方塊 您可以使用這個文字方塊來命名例外狀況變數。 例外狀況變數只能用於相同 **Catch** 內的活動。

**TryCatch** 設計師不支援編輯 **Catch**。 如果您想要變更例外狀況類型，則必須刪除 Catch 並加入新的 **Catch** 。 您可以藉由選取 Catch 來刪除它，或在以滑鼠右鍵按一下來存取的內容功能表上選取 [**刪除**] 來刪除 **Catch** 。

### <a name="the-trycatch-properties"></a>TryCatch 屬性

下表顯示 <xref:System.Activities.Statements.TryCatch> 屬性，並描述如何在設計工具中使用它們。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.TryCatch> 活動選用的易記名稱。 預設為 TryCatch。|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|否|當 <xref:System.Activities.Statements.TryCatch> 執行時，首先執行的活動。|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|否|當活動擲回例外狀況時，要檢查的 **Catch** 元素集合 <xref:System.Activities.Statements.TryCatch.Try%2A> 。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|否|當 <xref:System.Activities.Statements.TryCatch.Try%2A> 和 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中的任何必要活動完成執行時，要執行的活動。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [扔](../workflow-designer/throw-activity-designer.md)
