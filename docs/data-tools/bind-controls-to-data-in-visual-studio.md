---
title: 將控制項繫結至 Visual Studio 中的資料
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4100066d6c6b86bf319cad3bc123098835807acb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="bind-controls-to-data-in-visual-studio"></a>將控制項繫結至 Visual Studio 中的資料
您可以透過將資料繫結至控制項，對應用程式的使用者顯示資料。 您可以建立這些資料繫結控制項項目從**資料來源**視窗拖曳到設計介面或在 Visual Studio 中的介面上的控制項。

 這個主題描述可用來建立資料繫結控制項的資料來源。 此外，也描述與資料繫結相關的一些一般工作。 如需如何建立資料繫結控制項更具體的詳細資訊，請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)和[繫結 WPF 控制項加入 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

## <a name="data-sources"></a>資料來源
 在資料繫結的內容中，資料來源代表可繫結至您的使用者介面的記憶體中的資料。 實際上，資料來源可以是 Entity Framework 類別、 資料集、 封裝.NET proxy 物件，LINQ to SQL 類別或任何.NET 物件或集合中的服務端點。 某些資料來源可讓您建立資料繫結控制項中的項目**資料來源**視窗中，但不需要其他資料來源。 下表顯示支援的資料來源。

|資料來源|中的拖放支援**Windows Form 設計工具**|中的拖放支援**WPF 設計工具**|中的拖放支援**Silverlight Designer**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|資料集|[是]|是|否|
|實體資料模型|[是]<sup>1</sup>|[是]|[是]|
|LINQ to SQL 類別|否<sup>2</sup>|否<sup>2</sup>|否<sup>2</sup>|
|服務 (包括[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]，WCF 服務和 web 服務)|[是]|是|[是]|
|Object|[是]|是|[是]|
|SharePoint|[是]|是|[是]|

 1. 產生模型使用**實體資料模型**精靈，然後將這些物件拖曳至設計工具。

 2. LINQ to SQL 類別不會出現在**資料來源**視窗。 不過，您可以根據 LINQ to SQL 類別加入新的物件資料來源，然後將這些物件拖曳至設計工具，來建立資料繫結控制項。 如需詳細資訊，請參閱[逐步解說： 建立 LINQ to SQL 類別 （O R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。

## <a name="data-sources-window"></a>資料來源視窗
 資料來源可以是您的專案中的項目**資料來源**視窗。 此視窗是可見的或從存取**檢視**時表單的設計介面是您的專案中的現用視窗的功能表。 您可以在建立控制項繫結至基礎資料中，這個視窗拖曳項目，您也可以設定資料來源，以滑鼠右鍵按一下。

 ![資料來源視窗](../data-tools/media/raddata-data-sources-window.png "raddata 資料來源視窗")

 會出現在每種資料類型**資料來源**視窗中，預設會建立控制項時，您將項目拖曳至設計工具。 拖曳的項目之前**資料來源**視窗中，您可以變更將會建立的控制項。 如需詳細資訊，請參閱[設定要從資料來源視窗拖曳時建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

## <a name="tasks-involved-in-binding-controls-to-data"></a>將控制項繫結至資料的相關工作
 下表列出一些您執行的常見工作的控制項繫結至資料。

|工作|詳細資訊|
|----------|----------------------|
|開啟**資料來源**視窗。|在編輯器中開啟設計介面，然後選擇**檢視** > **資料來源**。|
|將資料來源加入至您的專案。|[新增資料來源](../data-tools/add-new-data-sources.md)|
|設定當您拖曳的項目時所建立的控制項**資料來源**至設計工具 視窗。|[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|修改中的項目相關聯的控制項清單**資料來源**視窗。|[將自訂控制項新增至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|建立資料繫結控制項。|[將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|繫結至物件或集合。|[Visual Studio 中的物件繫結](../data-tools/bind-objects-in-visual-studio.md)|
|UI 中顯示的篩選資料。|[在 Windows Forms 應用程式中篩選和排序資料](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|自訂控制項的標題。|[自訂 Visual Studio 為資料繫結的控制項建立標題的方式](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Forms 資料繫結](/dotnet/framework/winforms/windows-forms-data-binding)