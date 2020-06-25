---
title: 儲存前認可資料繫結控制項的同進程編輯
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f0369f4410c1eaf5a168a5291feebf64dbc9ee65
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282705"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>儲存資料前先認可資料繫結控制項上的同處理序編輯

編輯資料繫結控制項中的值時，使用者必須流覽目前的記錄，以便將更新的值認可至控制項所系結的基礎資料來源。 當您從 [[資料來源] 視窗](add-new-data-sources.md)將專案拖曳至表單時，您卸載的第一個專案會在的 [**儲存**] 按鈕 click 事件中產生程式碼 <xref:System.Windows.Forms.BindingNavigator> 。 這個程式碼會呼叫的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法 <xref:System.Windows.Forms.BindingSource> 。 因此， <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 只有 <xref:System.Windows.Forms.BindingSource> 新增至表單的第一個才會產生方法的呼叫。

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫會認可目前所編輯的任何資料繫結控制項中，所有正在進行的變更。 因此，當資料繫結控制項還有焦點時，您可以按一下 [儲存]**** 按鈕，就會在實際儲存 (`TableAdapterManager.UpdateAll` 方法) 之前，先認可該控制項中所有暫止的編輯項目。

您可以將應用程式設定為自動認可變更，即使使用者嘗試儲存資料而不認可變更，做為儲存過程的一部分。

> [!NOTE]
> 設計工具只會 `BindingSource.EndEdit` 為第一個放置在表單上的專案新增程式碼。 因此，您必須新增一行程式碼，以 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 針對表單上的每個呼叫方法 <xref:System.Windows.Forms.BindingSource> 。 您可以手動新增一行程式碼，為 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 每個呼叫方法 <xref:System.Windows.Forms.BindingSource> 。 或者，您可以將 `EndEditOnAllBindingSources` 方法加入至表單，並在執行儲存之前呼叫它。

下列程式碼會使用[LINQ （語言整合式查詢）](/dotnet/csharp/linq/)查詢來 <xref:System.Windows.Forms.BindingSource> 逐一查看所有元件，並 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> 在表單上呼叫每一個的方法。

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>為表單上的所有 BindingSource 元件呼叫 EndEdit

1. 將下列程式碼新增至包含元件的表單 <xref:System.Windows.Forms.BindingSource> 。

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. 在任何呼叫儲存表單的資料之前，立即新增下列程式程式碼（ `TableAdapterManager.UpdateAll()` 方法）：

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [階層式更新](../data-tools/hierarchical-update.md)
