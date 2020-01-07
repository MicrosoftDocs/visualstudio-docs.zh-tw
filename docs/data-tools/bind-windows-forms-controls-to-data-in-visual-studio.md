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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 244829edb30bbd43384ba445852f0a9ceafafb3f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587013"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>將 Windows Forms 控制項繫結至 Visual Studio 中的資料

您可以藉由將資料系結至 Windows Forms，向應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，請將專案從 [**資料來源**] 視窗拖曳至 Visual Studio 中的 Windows Form 設計工具。

![資料來源拖曳作業](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> 如果看不到 [**資料來源**] 視窗，您可以選擇 [ **View** > **其他 Windows** > **資料來源**]，或按**Shift**+**Alt**+**D**來開啟它。 您必須在 Visual Studio 中開啟專案，才能看到 [**資料來源**] 視窗。

在拖曳專案之前，您可以設定您想要系結的控制項類型。 視您選擇的是資料表本身還是個別資料行而定，會顯示不同的值。  您也可以設定自訂值。 對於資料表而言，[**詳細資料**] 表示每個資料行都系結至個別的控制項。

![將資料來源系結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 和 BindingNavigator 控制項

<xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 首先，它會在將控制項系結至資料時，提供抽象層。 表單上的控制項系結至 <xref:System.Windows.Forms.BindingSource> 元件，而不是直接系結至資料來源。 第二，它可以管理物件的集合。 將類型加入至 <xref:System.Windows.Forms.BindingSource> 會建立該類型的清單。

如需 <xref:System.Windows.Forms.BindingSource> 元件的詳細資訊，請參閱：

- [BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource 元件架構](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator 控制項](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)提供一個使用者介面，可供流覽 Windows 應用程式所顯示的資料。

## <a name="bind-to-data-in-a-datagridview-control"></a>系結至 DataGridView 控制項中的資料

針對[DataGridView 控制項](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)，整個資料表會系結至該單一控制項。 當您將**DataGridView**拖曳至表單時，也會出現導覽記錄的工具區域（<xref:System.Windows.Forms.BindingNavigator>）。 [資料集](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、<xref:System.Windows.Forms.BindingSource>和 <xref:System.Windows.Forms.BindingNavigator> 會出現在元件匣中。 在下圖中，也會加入[TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) ，因為 Customers 資料表與 Orders 資料表有關聯性。 這些變數都會在自動產生的程式碼中宣告為表單類別中的私用成員。 用來填入**DataGridView**的自動產生程式碼位於 `Form_Load` 事件處理常式中。 用來儲存資料以更新資料庫的程式碼位於**BindingNavigator**的 `Save` 事件處理常式中。 您可以視需要移動或修改此程式碼。

![GridView 與 BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

您可以按一下每個的右上角的智慧標籤，以自訂**DataGridView**和**BindingNavigator**的行為：

![DataGridView 和系結導覽器智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

如果您的應用程式所需的控制項無法在 [**資料來源**] 視窗中使用，您可以加入控制項。 如需詳細資訊，請參閱[將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

您也可以將專案從 [**資料來源**] 視窗拖曳至表單上的控制項，以將控制項系結至資料。 已經系結至資料的控制項，其資料系結會重設為最近拖曳至其上的專案。 若要成為有效的放置目標，控制項必須能夠顯示從 [**資料來源**] 視窗拖曳至該專案的基礎資料類型。 例如，將具有 <xref:System.DateTime> 資料類型的專案拖曳到 <xref:System.Windows.Forms.CheckBox>上是不正確，因為 <xref:System.Windows.Forms.CheckBox> 無法顯示日期。

## <a name="bind-to-data-in-individual-controls"></a>系結至個別控制項中的資料

當您將資料來源系結至**詳細**資料時，資料集中的每個資料行都會系結至個別的控制項。

![將資料來源系結至詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> 請注意，在上圖中，您可以從 [Customers] 資料表的 Orders 屬性拖曳，而不是從 [Orders] 資料表。 藉由系結至 `Customer.Orders` 屬性，在**DataGridView**中進行的導覽命令會立即反映在詳細資料控制項中。 如果您從 Orders 資料表拖曳，控制項仍然會系結至資料集，但不會與**DataGridView**同步處理。

下圖顯示在 [Customers] 資料表中的 Orders 屬性系結至 [**資料來源**] 視窗中的**詳細**資料之後，加入表單的預設資料繫結控制項。

![已系結至詳細資料的 Orders 資料表](../data-tools/media/raddata-orders-table-bound-to-details.png)

另請注意，每個控制項都有智慧標籤。 此標記會啟用僅適用于該控制項的自訂。

## <a name="see-also"></a>請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms （.NET Framework）中的資料系結](/dotnet/framework/winforms/windows-forms-data-binding)
