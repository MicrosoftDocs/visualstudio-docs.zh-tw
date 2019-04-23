---
title: 儲存資料前先認可資料繫結控制項上的同處理序編輯 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 813e49ab316f1fe74daa7a797dd6e16a878667d1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664579"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>儲存資料前先認可資料繫結控制項上的同處理序編輯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您編輯資料繫結控制項中的值，使用者必須瀏覽已更新的值認可到基礎資料來源控制項繫結至目前的資料錄。 當您拖曳項目從[資料來源 視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至表單，您卸除第一個項目會產生程式碼插入**儲存**按鈕的 click 事件的<xref:System.Windows.Forms.BindingNavigator>。 此程式碼會呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法的<xref:System.Windows.Forms.BindingSource>。 因此，呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法會產生只會針對第一個<xref:System.Windows.Forms.BindingSource>加入至表單。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫會認可目前所編輯的任何資料繫結控制項中，所有正在進行的變更。 因此，當資料繫結控制項還有焦點時，您可以按一下 [儲存] 按鈕，就會在實際儲存 (`TableAdapterManager.UpdateAll` 方法) 之前，先認可該控制項中所有暫止的編輯項目。  
  
 即使使用者嘗試儲存資料，而不需要認可變更，儲存的一部分，您可以設定您的應用程式會自動認可變更，處理程序。  
  
> [!NOTE]
>  設計工具新增`BindingSource.EndEdit`放到表單上的程式碼只會針對第一個項目。 因此，您必須新增一行程式碼以呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法，每個<xref:System.Windows.Forms.BindingSource>表單上。 您可以手動新增一行程式碼來呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法，每個<xref:System.Windows.Forms.BindingSource>。 或者，您可以在其中加入`EndEditOnAllBindingSources`方法加入表單並呼叫它，然後再執行儲存。  
  
 下列程式碼會使用[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)查詢，以逐一查看所有<xref:System.Windows.Forms.BindingSource>元件並呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法，每個<xref:System.Windows.Forms.BindingSource>表單上。  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>若要在表單上的所有 BindingSource 元件都呼叫 EndEdit  
  
1.  將下列程式碼新增至表單，其中包含<xref:System.Windows.Forms.BindingSource>元件。  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  新增下列程式碼，將表單的資料儲存的任何呼叫之前，立即 (`TableAdapterManager.UpdateAll()`方法):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [階層式更新](../data-tools/hierarchical-update.md)
