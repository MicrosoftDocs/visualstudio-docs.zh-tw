---
title: 儲存資料前先認可資料繫結控制項上的同處理序編輯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ffc192d5afc8540c60712192dc6d1af6135a2d66
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>儲存資料前先認可資料繫結控制項上的同處理序編輯
當編輯資料繫結控制項中的值，使用者必須瀏覽目前的資料錄控制項繫結至基礎資料來源認可更新的值。 當您拖曳項目從[資料來源視窗](add-new-data-sources.md)拖曳至表單，您卸除的第一個項目產生程式碼到**儲存**按鈕的 click 事件的<xref:System.Windows.Forms.BindingNavigator>。 此程式碼會呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法<xref:System.Windows.Forms.BindingSource>。 因此，呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法只會產生第一個<xref:System.Windows.Forms.BindingSource>加入至表單。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A>呼叫認可程序，在任何目前正在編輯的資料繫結控制項中的任何變更。 因此，如果資料繫結控制項還有焦點時，您可以按一下**儲存**按鈕，所有暫止的編輯控制項之前，在實際儲存先認可，(`TableAdapterManager.UpdateAll`方法)。  
  
 您可以設定自動認可變更，您的應用程式，即使使用者嘗試儲存資料而不儲存一部分認可變更，程序。  
  
> [!NOTE]
>  設計工具加入`BindingSource.EndEdit`放到表單上的程式碼，僅針對第一個項目。 因此，您必須加入一行程式碼以呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>每個方法<xref:System.Windows.Forms.BindingSource>表單上。 您可以手動加入一行呼叫的程式碼<xref:System.Windows.Forms.BindingSource.EndEdit%2A>每個方法<xref:System.Windows.Forms.BindingSource>。 或者，您可以新增`EndEditOnAllBindingSources`方法加入表單並執行儲存之前，先呼叫它。  
  
 下列程式碼會使用[LINQ (Language-Integrated Query ()](/dotnet/csharp/linq/)來逐一查看所有的查詢<xref:System.Windows.Forms.BindingSource>元件並呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>每個方法<xref:System.Windows.Forms.BindingSource>表單上。  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>若要呼叫 EndEdit 表單上的所有 BindingSource 元件  
  
1.  將下列程式碼加入至表單，以包含<xref:System.Windows.Forms.BindingSource>元件。  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  加入下列程式碼之前要儲存表單資料的任何呼叫 (`TableAdapterManager.UpdateAll()`方法):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [階層式更新](../data-tools/hierarchical-update.md)