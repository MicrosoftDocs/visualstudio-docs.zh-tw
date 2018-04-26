---
title: Windows Form 控制項繫結至 Visual Studio 中的資料
ms.date: 11/03/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e89a919f6f93dc70f9417a23430c960f03cf92bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Windows Form 控制項繫結至 Visual Studio 中的資料
您可以加入 Windows Form 資料繫結，您的應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，您可以將項目從**資料來源**視窗拖曳至 Visual Studio 中的 Windows Form 設計工具。

![資料來源拖曳作業](../data-tools/media/raddata-data-source-drag-operation.png "raddata 資料來源拖曳作業")

您拖曳項目之前，您可以設定您想要繫結至控制項的類型。 根據您選擇本身，或個別的資料行的資料表會出現不同的值。  您也可以設定自訂值。 [詳細資料] 資料表，表示每個資料行的繫結至個別的控制項。

![資料來源繫結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "DataGridView raddata 繫結資料來源")

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 和 BindingNavigator 控制項
<xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 首先，它會提供一個抽象層時將控制項繫結至資料。 表單上的控制項繫結至<xref:System.Windows.Forms.BindingSource>元件而不是直接到資料來源。 第二，它可以管理物件的集合。 將類型加入<xref:System.Windows.Forms.BindingSource>建立該類型的清單。

如需有關<xref:System.Windows.Forms.BindingSource>元件，請參閱：

-   [BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)

-   [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [BindingSource 元件架構](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator 控制項](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)提供使用者介面來瀏覽 Windows 應用程式所顯示的資料。

## <a name="bind-to-data-in-a-datagridview-control"></a>繫結至 DataGridView 控制項中的資料
如[DataGridView 控制項](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)，整個資料表繫結至該單一的控制項。 當您將 DataGridView 拖曳至表單時，工具帶狀用於巡覽資料錄 (<xref:System.Windows.Forms.BindingNavigator>) 也會出現。 A[資料集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/create-and-configure-tableadapters.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>出現在元件匣中。 在下圖中，因為客戶資料表 Orders 資料表的關聯性，也會加入 TableAdapterManager。 這些變數是所有宣告在自動產生程式碼為表單類別中的私用成員。 自動產生的程式碼，以便填滿 DataGridView 位於 form_load 事件處理常式。 儲存更新的資料庫資料的程式碼位於 BindingNavigator 儲存事件處理常式。 您可以移動，或視需要修改這個程式碼。

![GridView BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView BindingNavigator")

您可以自訂和行為的 DataGridView BindingNavigator 上的每個右角的智慧標籤，即可：

![DataGridView 和繫結導覽智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 和繫結導覽智慧標籤")

如果控制項應用程式需求不是可從**資料來源**視窗中，您可以將控制項。 如需詳細資訊，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

您也可以拖曳項目從**資料來源**視窗拖曳至表單，以將控制項繫結至資料上的控制項。 已繫結至資料的控制項已的資料繫結重設為最近拖曳至其本身的項目。 若要有效置放目標，控制項必須是可顯示基礎資料類型的項目拖曳到從**資料來源**視窗。 例如，不能將具有資料類型的項目拖曳<xref:System.DateTime>到<xref:System.Windows.Forms.CheckBox>，因為<xref:System.Windows.Forms.CheckBox>不是可顯示日期。

## <a name="bind-to-data-in-individual-controls"></a>繫結至個別控制項中的資料
當您將資料來源繫結至 [詳細資料] 會在資料集中的每個資料行繫結至個別的控制項。

![資料來源繫結詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 繫結資料來源詳細資料")

> [!IMPORTANT]
> 請注意，在上圖中，您將從 Customers 資料表中，不是從 「 訂單 」 資料表中的 [訂單] 屬性。 繫結至 Customer.Orders 屬性，在 DataGridView 中進行巡覽命令會立即反映在詳細資料控制項。 如果您拖曳 Orders 資料表中，控制項仍然會繫結至資料集，但沒有它們就不會同步 DataGridView。

下圖顯示預設資料繫結控制項的 Customers 資料表中的 Orders 屬性繫結至 [詳細資料] 之後才加入至表單中**資料來源**視窗。

![Orders 資料表繫結至詳細資料](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 資料表繫結至詳細資料")

請注意每個控制項具有智慧標籤。 這個標記可讓該控制項只會套用的自訂項目。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [在 Windows Form (.NET Framework) 中的資料繫結](/dotnet/framework/winforms/windows-forms-data-binding)