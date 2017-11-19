---
title: "Windows Form 應用程式建立查閱資料表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 00686648576ecc0f8054fe56112c5c47bb54adb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Form 應用程式建立查閱資料表
詞彙*查閱資料表*描述繫結至兩個關聯的資料表的控制項。 這些查閱控制項顯示資料的第一個資料表，根據在第二個資料表中選取的值。  
  
 您可以透過將主要節點的父資料表中建立查閱資料表 (從[資料來源視窗](add-new-data-sources.md)) 拖曳至表單中相關的子資料表的資料行已繫結的控制項。  
  
 例如，假設資料表的`Orders`銷售資料庫中。 在每一筆記錄`Orders`資料表包含`CustomerID`，指出哪位客戶下訂單。 `CustomerID`為外部索引鍵中的客戶記錄為指向`Customers`資料表。 在此案例中，展開`Orders`資料表中**資料來源**視窗並將主節點設定為**詳細資料**。 然後設定`CustomerID`資料行使用<xref:System.Windows.Forms.ComboBox>（或任何其他支援對應繫結的控制項），並拖曳`Orders`節點拖曳至表單。 最後，將`Customers`節點拖曳至控制項繫結至相關的資料行-在此情況下，<xref:System.Windows.Forms.ComboBox>繫結至`CustomerID`資料行。  
  
## <a name="to-databind-a-lookup-control"></a>資料繫結的查閱控制項  
  
1.  開啟**資料來源**視窗。  
  
    > [!NOTE]
    >  查閱資料表，都需要兩個相關的資料表或物件會提供**資料來源**視窗。 如需詳細資訊，請參閱[集中的關聯性](relationships-in-datasets.md)。  
  
2.  展開中的節點**資料來源**視窗內，直到您可以看到父資料表和其資料行和關聯的子資料表與所有的資料行。  
  
    > [!NOTE]
    >  子資料表節點是父資料表中的可展開的子節點形式出現的節點。  
  
3.  子資料表卸除類型變更**詳細資料**選取**詳細資料**子資料表節點上的控制項清單中。 如需詳細資訊，請參閱[設定要從資料來源視窗拖曳時建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
4.  找出與兩個資料表相關的節點 (`CustomerID`前一個範例中的節點)。將其卸除類型變更<xref:System.Windows.Forms.ComboBox>選取**ComboBox**的控制項清單中。  
  
5.  從主要子資料表節點拖曳**資料來源**視窗拖曳至表單。  
  
     資料繫結控制項 （具有描述性標籤） 和工具帶狀 (<xref:System.Windows.Forms.BindingNavigator>) 顯示在表單上。 A[資料集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/create-and-configure-tableadapters.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>出現在元件匣中。  
  
6.  現在將主要父資料表節點，從**資料來源**視窗直接拖曳到查閱控制項 ( <xref:System.Windows.Forms.ComboBox>)。  
  
     如此就會建立查閱繫結。 請參閱下表的控制項所設定的特定屬性。  
  
    |屬性|設定說明|  
    |--------------|----------------------------|  
    |**資料來源**|Visual Studio 會將此屬性設定為針對您拖曳至控制項之資料表所建立的 <xref:System.Windows.Forms.BindingSource> (與建立控制項時所建立的 <xref:System.Windows.Forms.BindingSource> 相反)。<br /><br /> 如果您需要進行調整，然後將此設<xref:System.Windows.Forms.BindingSource>具有您想要顯示的資料行的資料表。|  
    |**DisplayMember**|Visual Studio 會將此屬性設定為主索引鍵後面具有字串資料類型的第一個資料行 (針對您拖曳至控制項的資料表)。<br /><br /> 如果您需要進行調整，然後設定為您想要顯示的資料行名稱。|  
    |**ValueMember**|Visual Studio 會將此屬性設定為參與主索引鍵的第一個資料行，或者，如果未定義索引鍵，則為資料表中的第一個資料行。<br /><br /> 如果您需要進行調整，然後設定為您想要顯示的資料行的資料表中的主索引鍵。|  
    |**SelectedValue**|Visual Studio 會將此屬性設定為從卸除原始的資料行**資料來源**視窗。<br /><br /> 如果您需要進行調整，然後設定為相關資料表中的外部索引鍵資料行。|  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)