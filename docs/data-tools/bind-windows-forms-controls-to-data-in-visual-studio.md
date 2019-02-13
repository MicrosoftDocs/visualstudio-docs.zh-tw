---
title: 將 Windows Forms 控制項繫結至資料
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b961af0bf35bb4476f9f336fcf5298bb0bd3651
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951666"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>將 Windows Forms 控制項繫結至 Visual Studio 中的資料

您可以藉由將資料繫結至 Windows Forms 應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，將 項目從**Zdroje dat**視窗拖曳至 Visual Studio 中的 Windows Form 設計工具。

![資料來源拖放作業](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> 如果**資料來源**視窗未顯示，您可以選擇來開啟**檢視** > **其他 Windows** > **資料來源**，或按下**Shift**+**Alt**+**D**。 您必須有專案，若要查看 Visual Studio 中開啟**Zdroje dat**視窗。

您拖曳項目之前，您可以設定您想要繫結至控制項的型別。 根據您選擇本身，或個別資料行的資料表會顯示不同的值。  您也可以設定自訂值。 資料表中，**詳細資料**表示每個資料行繫結不同的控制項。

![資料來源繫結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 和 BindingNavigator 控制項


  <xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 首先，它提供一個抽象層時的控制項繫結至資料。 在表單上的控制項繫結至<xref:System.Windows.Forms.BindingSource>而不是直接對資料來源元件。 其次，它可以管理物件的集合。 將類型加入<xref:System.Windows.Forms.BindingSource>會建立該類型的清單。

如需詳細資訊<xref:System.Windows.Forms.BindingSource>元件，請參閱：

- [BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource 元件架構](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator 控制項](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)提供使用者介面來瀏覽 Windows 應用程式顯示的資料。

## <a name="bind-to-data-in-a-datagridview-control"></a>繫結至 DataGridView 控制項中的資料

針對[DataGridView 控制項](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)，整份資料表繫結至該單一控制項。 當您拖曳**DataGridView**表單中，巡覽記錄中刪除工具 (<xref:System.Windows.Forms.BindingNavigator>) 也會出現。 A[資料集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/create-and-configure-tableadapters.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。 在下圖中， [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx)也會加入，因為 「 客戶 」 資料表具有與 [Orders] 資料表的關聯性。 這些變數是所有宣告中的自動產生的程式碼為表單類別中的私用成員。 自動產生的程式碼，用於填滿**DataGridView**位於`Form_Load`事件處理常式。 儲存的資料，以更新資料庫的程式碼位於`Save`事件處理常式**BindingNavigator**。 您可以移動，或視需要修改此程式碼。

![使用 BindingNavigator 的 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

您可以自訂的行為**DataGridView**並**BindingNavigator**每個畫面右上角的智慧標籤，即可：

![DataGridView 和繫結的巡覽器的智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

您的應用程式需求且沒有控制可從**Zdroje dat**  視窗中，您可以將控制項。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

您也可以拖曳項目從**Zdroje dat**視窗拖曳至已在控制項繫結至資料的表單上的控制項。 已繫結至資料的控制項具有其資料繫結重設為最近拖曳的項目。 若要有效置放目標，控制項必須是可顯示基礎資料類型的項目拖曳至從**Zdroje dat**視窗。 比方說，不拖曳項目具有資料類型的有效<xref:System.DateTime>拖曳至<xref:System.Windows.Forms.CheckBox>，因為<xref:System.Windows.Forms.CheckBox>不能顯示日期。

## <a name="bind-to-data-in-individual-controls"></a>繫結至個別控制項中的資料

當您繫結至資料來源**詳細資料**，在資料集中的每個資料行繫結至不同的控制項。

![資料來源繫結詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> 請注意，在上圖中，您將從 [客戶] 資料表中，不是從 「 訂單 」 資料表中的 [訂單] 屬性。 藉由繫結`Customer.Orders`中所做的屬性，瀏覽命令**DataGridView**會立即反映在 詳細資料控制項。 如果您從 [Orders] 資料表拖曳，控制項就仍然繫結至資料集，但不是會不會同步處理，則使用**DataGridView**。

下圖顯示的預設資料繫結控制項的 Customers 資料表中的 Orders 屬性繫結至之後才加入至表單**詳細資料**中**Zdroje dat**視窗。

![Orders 資料表繫結至詳細資料](../data-tools/media/raddata-orders-table-bound-to-details.png)

也請注意，每個控制項有智慧標籤。 這個標記可讓該控制項只適用於自訂項目。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [在 Windows Form (.NET Framework) 中的資料繫結](/dotnet/framework/winforms/windows-forms-data-binding)