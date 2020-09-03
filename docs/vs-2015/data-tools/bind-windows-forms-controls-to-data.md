---
title: 將 Windows Forms 控制項系結至資料 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672969"
---
# <a name="bind-windows-forms-controls-to-data"></a>將 Windows Forms 控制項繫結至資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將物件從 [ **資料來源** ] 視窗拖曳至 Windows form 上，或拖曳至表單上的現有控制項，將資料來源系結至控制項。 拖曳專案之前，您可以設定要系結的控制項類型。 根據您選擇的是資料表本身或個別資料行，會顯示不同的值。  您也可以設定自訂值。 針對資料表，「詳細資料」表示每個資料行都系結至不同的控制項。

 ![將資料來源系結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata 將資料來源系結至 DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>系結至 DataGridView 控制項中的資料
 就 DataGridView 而言，整個資料表都會系結至該單一控制項。 當您將 DataGridView 拖曳至表單時，也會出現導覽記錄 () 的工具區域 <xref:System.Windows.Forms.BindingNavigator> 。 [資料集](../data-tools/dataset-tools-in-visual-studio.md)、TableAdapter、 <xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 都會出現在元件匣中。 在下圖中，也會加入 TableAdapterManager，因為 Customers 資料表與 Orders 資料表具有關聯性。 這些變數全都在自動產生的程式碼中宣告為 form 類別中的私用成員。 用於填滿 DataGridView 的自動產生程式碼位於 form_load 事件處理常式中。 用來儲存資料以更新資料庫的程式碼位於 BindingNavigator 的儲存事件處理常式中。 您可以視需要移動或修改此程式碼。

 ![GridView 與 BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "使用 BindingNavigator raddata GridView")

 您可以藉由按一下每個按鈕右上角的智慧標籤來自訂 DataGridView 和 BindingNavigator 的行為：

 ![DataGridView 和系結導覽器智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 和系結導覽器智慧標籤")

 如果您的應用程式所需的控制項無法從 [ **資料來源** ] 視窗中使用，您可以加入控制項。 如需詳細資訊，請參閱 [將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

 您也可以將專案從 [ **資料來源** ] 視窗拖曳至表單上的控制項，以將控制項系結至資料。 已經系結至資料的控制項，其資料系結會重設為最近拖曳至其上的專案。 若要成為有效的放置目標，控制項必須能夠顯示從 [ **資料來源** ] 視窗拖曳至其上之專案的基礎資料類型。 例如，將資料類型為的專案拖曳到上是不正確 <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> ，因為 <xref:System.Windows.Forms.CheckBox> 無法顯示日期。

## <a name="bind-to--data-in-individual-controls"></a>系結至個別控制項中的資料
 當您將資料來源系結至 [詳細資料] 時，資料集中的每個資料行會系結至不同的控制項。

 ![將資料來源系結至詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 將資料來源系結至詳細資料")

> [!IMPORTANT]
> 請注意，在上圖中，您會從 Customers 資料表的 Orders 屬性（而不是從 Orders 資料表）拖曳。 藉由系結至 Customer. Orders 屬性，在 DataGridView 中所做的導覽命令會立即反映在詳細資料控制項中。 如果您從 Orders 資料表拖曳，控制項仍會系結至資料集，但不會與 DataGridView 進行同步處理。

 下圖顯示在 Customers 資料表中的 Orders 屬性系結至 [ **資料來源** ] 視窗中的 [詳細資料] 之後，加入至表單的預設資料繫結控制項。

 ![訂單資料表系結至詳細資料](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 資料表系結至詳細資料")

 另外也請注意，每個控制項都有一個智慧標籤。 此標記只會啟用套用至該控制項的自訂。

## <a name="see-also"></a>另請參閱
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
