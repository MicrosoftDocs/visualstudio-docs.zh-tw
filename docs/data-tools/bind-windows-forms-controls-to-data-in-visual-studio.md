---
title: 將 Windows Forms 控制項繫結至資料
description: 將 Windows Forms 控制項系結至 Visual Studio 中的資料，讓您可以向應用程式的使用者顯示資料。
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3da0c4e9835c9b6f6498aa28b82f2e631d1717ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867408"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>將 Windows Forms 控制項繫結至 Visual Studio 中的資料

您可以藉由將資料系結至 Windows Forms，向應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，請將專案從 [ **資料來源** ] 視窗拖曳至 Visual Studio 中的 Windows Form 設計工具。

![資料來源拖曳操作](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> 如果看不到 [**資料來源**] 視窗，您可以選擇 [ **View**  >  **Other Windows**  >  **資料來源**]，或按 **Shift** + **Alt** + **D** 來開啟它。 您必須在 Visual Studio 中開啟專案，才能看到 [ **資料來源** ] 視窗。

拖曳專案之前，您可以設定要系結的控制項類型。 根據您選擇的是資料表本身或個別資料行，會顯示不同的值。  您也可以設定自訂值。 針對資料表， **詳細資料** 表示每個資料行都系結至不同的控制項。

![將資料來源系結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 和 BindingNavigator 控制項

<xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 首先，它會在將控制項系結至資料時提供抽象層。 表單上的控制項系結至 <xref:System.Windows.Forms.BindingSource> 元件，而不是直接系結至資料來源。 其次，它可以管理物件的集合。 將型別加入至 <xref:System.Windows.Forms.BindingSource> 會建立該型別的清單。

如需元件的詳細資訊 <xref:System.Windows.Forms.BindingSource> ，請參閱：

- [BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource 元件總覽](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource 元件架構](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator 控制項](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)提供使用者介面，可讓您流覽 Windows 應用程式所顯示的資料。

## <a name="bind-to-data-in-a-datagridview-control"></a>系結至 DataGridView 控制項中的資料

在 [DataGridView 控制項](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)中，整個資料表都會系結至該單一控制項。 當您將 **DataGridView** 拖曳至表單時，也會出現導覽記錄 () 的工具區域 <xref:System.Windows.Forms.BindingNavigator> 。 [資料集](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、 <xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 都會出現在元件匣中。 在下圖中，也會加入 [TableAdapterManager](/previous-versions/bb384426(v=vs.140)) ，因為 Customers 資料表與 Orders 資料表具有關聯性。 這些變數全都在自動產生的程式碼中宣告為 form 類別中的私用成員。 用於填滿 **DataGridView** 的自動產生程式碼位於 `Form_Load` 事件處理常式中。 用來儲存資料以更新資料庫的程式碼位於 `Save` **BindingNavigator** 的事件處理常式中。 您可以視需要移動或修改此程式碼。

![GridView 與 BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

您可以藉由按一下每個按鈕右上角的智慧標籤來自訂 **DataGridView** 和 **BindingNavigator** 的行為：

![DataGridView 和系結導覽器智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

如果您的應用程式所需的控制項無法從 [ **資料來源** ] 視窗中使用，您可以加入控制項。 如需詳細資訊，請參閱 [將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

您也可以將專案從 [ **資料來源** ] 視窗拖曳至表單上的控制項，以將控制項系結至資料。 已經系結至資料的控制項，其資料系結會重設為最近拖曳至其上的專案。 若要成為有效的放置目標，控制項必須能夠顯示從 [ **資料來源** ] 視窗拖曳至其上之專案的基礎資料類型。 例如，將資料類型為的專案拖曳到上是不正確 <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> ，因為 <xref:System.Windows.Forms.CheckBox> 無法顯示日期。

## <a name="bind-to-data-in-individual-controls"></a>系結至個別控制項中的資料

當您將資料來源系結至 **詳細** 資料時，資料集中的每個資料行都會系結至個別的控制項。

![將資料來源系結至詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> 請注意，在上圖中，您會從 Customers 資料表的 Orders 屬性（而不是從 Orders 資料表）拖曳。 藉由系 `Customer.Orders` 結至屬性， **DataGridView** 中所建立的導覽命令會立即反映在詳細資料控制項中。 如果您從 Orders 資料表拖曳，控制項仍會系結至資料集，但不會與 **DataGridView** 進行同步處理。

下圖顯示在 [Customers] 資料表的 Orders 屬性系結至 [**資料來源**] 視窗中的 **詳細** 資料之後，加入至表單的預設資料繫結控制項。

![訂單資料表系結至詳細資料](../data-tools/media/raddata-orders-table-bound-to-details.png)

另外也請注意，每個控制項都有一個智慧標籤。 此標記只會啟用套用至該控制項的自訂。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms ( .NET Framework 中的資料系結) ](/dotnet/framework/winforms/windows-forms-data-binding)