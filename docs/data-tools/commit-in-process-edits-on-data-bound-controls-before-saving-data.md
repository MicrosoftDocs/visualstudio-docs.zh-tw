---
title: 未認可的編輯
description: 儲存資料之前，請先認可資料系結 Windows Forms 控制項的同進程編輯。 針對表單上的所有 BindingSource 元件呼叫 EndEdit。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 98f75769a8002fd960da74dc5f9bd9a6b046a604
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867239"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>儲存資料前先認可資料繫結控制項上的同處理序編輯

編輯資料繫結控制項中的值時，使用者必須流覽目前的記錄，以將更新的值認可至控制項所系結的基礎資料來源。 當您將專案從 [ [資料來源] 視窗](add-new-data-sources.md) 拖曳到表單上時，您卸載的第一個專案會產生程式碼到的 [ **儲存** ] 按鈕 click 事件中 <xref:System.Windows.Forms.BindingNavigator> 。 此程式碼會呼叫的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法 <xref:System.Windows.Forms.BindingSource> 。 因此， <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 只會針對 <xref:System.Windows.Forms.BindingSource> 加入至表單的第一個來產生方法的呼叫。

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫會認可目前所編輯的任何資料繫結控制項中，所有正在進行的變更。 因此，當資料繫結控制項還有焦點時，您可以按一下 [儲存] 按鈕，就會在實際儲存 (`TableAdapterManager.UpdateAll` 方法) 之前，先認可該控制項中所有暫止的編輯項目。

您可以將應用程式設定為自動認可變更，即使使用者嘗試在不認可變更的情況下儲存資料，做為儲存流程的一部分。

> [!NOTE]
> 設計工具只會 `BindingSource.EndEdit` 為第一個放置在表單上的專案加入程式碼。 因此，您必須加入一行程式碼，以 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 針對表單上的每個呼叫方法 <xref:System.Windows.Forms.BindingSource> 。 您可以手動新增一行程式碼，以呼叫 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 每個程式碼的方法 <xref:System.Windows.Forms.BindingSource> 。 或者，您可以將 `EndEditOnAllBindingSources` 方法新增至表單，並在執行儲存之前呼叫它。

下列程式碼會使用 [LINQ (語言整合查詢) ](/dotnet/csharp/linq/) 查詢來 <xref:System.Windows.Forms.BindingSource> 逐一查看所有元件，並 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> 在表單上呼叫每個元件的方法。

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>為表單上的所有 BindingSource 元件呼叫 EndEdit

1. 將下列程式碼新增至包含元件的表單 <xref:System.Windows.Forms.BindingSource> 。

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. 將下列程式程式碼緊接在 (方法) 儲存表單資料的任何呼叫之前 `TableAdapterManager.UpdateAll()` ：

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [階層式更新](../data-tools/hierarchical-update.md)
