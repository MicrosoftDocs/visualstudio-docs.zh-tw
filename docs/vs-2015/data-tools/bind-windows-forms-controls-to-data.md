---
title: Windows Forms 控制項繫結至資料 |Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9b81d3d9f7425874c8a3501d8e1d49eb813b97d9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943127"
---
# <a name="bind-windows-forms-controls-to-data"></a>將 Windows Forms 控制項繫結至資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以將物件從資料來源繫結至控制項**Zdroje dat**視窗拖曳至 Windows 表單或表單上的現有控制項。 您拖曳項目之前，您可以設定您想要繫結至控制項的型別。 根據您選擇本身，或個別資料行的資料表會顯示不同的值。  您也可以設定自訂值。 [詳細資料] 資料表，表示每個資料行繫結不同的控制項。  
  
 ![資料來源繫結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "DataGridView raddata 繫結資料來源")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>繫結至 DataGridView 控制項中的資料  
 DataGridView 中，整份資料表是繫結至該單一控制項。 當您將 DataGridView 拖曳至表單時，工具帶狀巡覽記錄 (<xref:System.Windows.Forms.BindingNavigator>) 也會出現。 A[資料集](../data-tools/dataset-tools-in-visual-studio.md)，TableAdapter，並<xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。 在下圖中，因為 「 客戶 」 資料表具有與 [Orders] 資料表的關聯性，也會加入 TableAdapterManager。 這些變數是所有宣告中的自動產生的程式碼為表單類別中的私用成員。 自動產生的程式碼，以便填滿 DataGridView 位於 form_load 事件處理常式。 儲存的資料，以更新資料庫的程式碼位於 BindingNavigator 儲存事件處理常式。 您可以移動，或視需要修改此程式碼。  
  
 ![使用 BindingNavigator 的 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata 使用 BindingNavigator 的 GridView")  
  
 您可以在每個右上角的智慧標籤，即可自訂 DataGridView 和 BindingNavigator 的行為：  
  
 ![DataGridView 和繫結的導覽器智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 和繫結的導覽器智慧標籤")  
  
 您的應用程式需求且沒有控制可從**Zdroje dat**  視窗中，您可以將控制項。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
 您也可以拖曳項目從**Zdroje dat**視窗拖曳至已在控制項繫結至資料的表單上的控制項。 已繫結至資料的控制項具有其資料繫結重設為最近拖曳的項目。 若要有效置放目標，控制項必須是可顯示基礎資料類型的項目拖曳至從**Zdroje dat**視窗。 比方說，不拖曳項目具有資料類型的有效<xref:System.DateTime>拖曳至<xref:System.Windows.Forms.CheckBox>，因為<xref:System.Windows.Forms.CheckBox>不能顯示日期。  
  
## <a name="bind-to--data-in-individual-controls"></a>繫結至個別控制項中的資料  
 當您將資料來源繫結至 [詳細資料] 時，會在資料集中的每個資料行繫結至不同的控制項。  
  
 ![資料來源繫結詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 繫結資料來源詳細資料")  
  
> [!IMPORTANT]
>  請注意，在上圖中，您將從 [客戶] 資料表中，不是從 「 訂單 」 資料表中的 [訂單] 屬性。 藉由 Customer.Orders 屬性繫結，在 DataGridView 中所做的巡覽命令會立即反映在詳細資料控制項。 如果您從 [Orders] 資料表拖曳時，控制項就仍然繫結至資料集，但不是會不會同步處理，則使用 DataGridView。  
  
 下圖顯示的預設資料繫結控制項的 Customers 資料表中的 Orders 屬性繫結至 [詳細資料] 之後才加入至表單中**Zdroje dat**視窗。  
  
 ![Orders 資料表繫結至詳細資料](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 資料表繫結至詳細資料")  
  
 也請注意，每個控制項有智慧標籤。 這個標記可讓該控制項只適用於自訂項目。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
