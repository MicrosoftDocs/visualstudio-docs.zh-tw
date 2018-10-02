---
title: 在 Windows Forms 應用程式中建立查閱資料表 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a61286dee857f6e8f08a815e6058ce1761a646bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491889"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>在 Windows Forms 應用程式中建立查閱資料表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[在 Windows Forms 應用程式中建立查閱資料表](https://docs.microsoft.com/visualstudio/data-tools/create-lookup-tables-in-windows-forms-applications)。  
  
  
詞彙*查閱資料表*描述繫結至兩個相關的資料表的控制項。 這些查閱控制項顯示從第二個資料表中選取的值為基礎的第一個資料表的資料。  
  
 您可以藉由拖曳父資料表的主要節點建立查閱資料表 (從[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) 拖曳至表單中的相關的子資料表的資料行已繫結的控制項。  
  
 例如，假設資料表的`Orders`銷售資料庫中。 在每一筆記錄`Orders`資料表包含`CustomerID`，指出哪些客戶下過訂單。 `CustomerID`指向中的客戶記錄為外部索引鍵`Customers`資料表。 在此案例中，您會擴充`Orders`資料表中**資料來源** 視窗並將主節點設定為**詳細資料**。 然後設定`CustomerID`若要使用的資料行<xref:System.Windows.Forms.ComboBox>（或任何其他支援查閱繫結的控制項），並將拖曳`Orders`節點拖曳至表單。 最後，拖曳`Customers`節點拖曳至控制項繫結至相關的資料行，在此情況下，<xref:System.Windows.Forms.ComboBox>繫結至`CustomerID`資料行。  
  
## <a name="to-databind-a-lookup-control"></a>資料繫結的查閱控制項  
  
1.  開啟**Zdroje dat**視窗。  
  
    > [!NOTE]
    >  查閱資料表需要兩個相關的資料表或物件會提供**Zdroje dat**視窗。 如需詳細資訊，請參閱[如何：在 Windows Forms 應用程式中顯示相關的資料](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)。  
  
2.  展開中的節點**Zdroje dat**視窗內，直到您可以看到父資料表和所有其資料行和關聯的子資料表和其所有資料行。  
  
    > [!NOTE]
    >  子資料表節點是會顯示為父資料表中的可展開的子節點的節點。  
  
3.  變更子資料表的卸除類型**詳細資料**藉由選取**詳細資料**子資料表的節點上的控制項清單。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
4.  找出相關的兩個資料表的節點 (`CustomerID`在上述範例中的節點)。將其卸除類型變更<xref:System.Windows.Forms.ComboBox>藉由選取**ComboBox**從控制項清單。  
  
5.  從主要子資料表節點拖曳**Zdroje dat**視窗拖曳至表單。  
  
     資料繫結控制項 （具有描述性的標籤） 和工具帶狀 (<xref:System.Windows.Forms.BindingNavigator>) 在表單上顯示。 A[資料集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/tableadapter-overview.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
6.  現在將從主要的父資料表節點拖曳**資料來源**視窗直接拖曳查閱控制項 ( <xref:System.Windows.Forms.ComboBox>)。  
  
     現在建立查閱繫結。 請參閱下表中的控制項所設定的特定屬性。  
  
    |屬性|設定說明|  
    |--------------|----------------------------|  
    |**DataSource**|Visual Studio 會將此屬性設定為針對您拖曳至控制項之資料表所建立的 <xref:System.Windows.Forms.BindingSource> (與建立控制項時所建立的 <xref:System.Windows.Forms.BindingSource> 相反)。<br /><br /> 如果您需要進行調整，然後將此設<xref:System.Windows.Forms.BindingSource>具有您想要顯示的資料行的資料表。|  
    |**DisplayMember**|Visual Studio 會將此屬性設定為主索引鍵後面具有字串資料類型的第一個資料行 (針對您拖曳至控制項的資料表)。<br /><br /> 如果您需要進行調整，則這設為您想要顯示的資料行名稱。|  
    |**ValueMember**|Visual Studio 會將此屬性設定為參與主索引鍵的第一個資料行，或者，如果未定義索引鍵，則為資料表中的第一個資料行。<br /><br /> 如果您需要進行調整，則此設定為含有您想要顯示的資料行的資料表的主索引鍵。|  
    |**SelectedValue**|Visual Studio 會將此屬性設定為從卸除原始的資料行**Zdroje dat**視窗。<br /><br /> 如果您需要進行調整，則此設定為相關資料表中的外部索引鍵資料行。|  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

