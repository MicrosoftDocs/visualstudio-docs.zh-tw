---
title: 將控制項繫結至資料
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
ms.openlocfilehash: c4e27f5ce9536e7128330ebe932709a9be408b7e
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305259"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>將控制項繫結至 Visual Studio 中的資料

您可以透過將資料繫結至控制項，對應用程式的使用者顯示資料。 您可以建立這些資料繫結控制項項目從**Zdroje dat**視窗拖曳到設計介面或在 Visual Studio 中的介面上的控制項。

這個主題描述可用來建立資料繫結控制項的資料來源。 此外，也描述與資料繫結相關的一些一般工作。 如需如何建立資料繫結控制項更具體的詳細資訊，請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)並[繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

## <a name="data-sources"></a>資料來源

在資料繫結內容中，資料來源代表可繫結至您的使用者介面的記憶體中的資料。 實際上，資料來源可以是 Entity Framework 類別、 資料集、 封裝.NET proxy 物件、 LINQ to SQL 類別，或任何.NET 物件或集合中的服務端點。 有些資料來源可讓您從 [資料來源 **] 視窗拖曳項目，以建立資料繫結程序控制項，有些資料來源則否。 下表顯示支援的資料來源。

| 資料來源 | Windows Form 設計工具**的拖放支援 | WPF 設計工具**的拖放支援 | Silverlight Designer** 的拖放支援 |
| - | - | - | - |
| 資料集 | [是] | [是] | 否 |
| 實體資料模型 | 是<sup>1</sup> | [是] | [是] |
| LINQ to SQL 類別 | 否<sup>2</sup> | 否<sup>2</sup> | 否<sup>2</sup> |
| 服務 (包括 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、Web 服務和 Web 服務) | [是] | [是] | [是] |
| Object | [是] | [是] | [是] |
| SharePoint | [是] | [是] | [是] |

1. 產生模型使用**Entity Data Model**精靈，然後將這些物件拖曳至設計工具。

2. LINQ to SQL 類別不會出現在 [資料來源 **] 視窗中。 不過，您可以根據 LINQ to SQL 類別加入新的物件資料來源，然後將這些物件拖曳至設計工具，來建立資料繫結控制項。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立的 LINQ to SQL 類別 （O-R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。

## <a name="data-sources-window"></a>資料來源視窗

資料來源會在 [資料來源 **] 視窗中以項目形式使用於專案。 表單設計介面是在專案中，使用中的視窗或您可以選擇來開啟它 （開啟專案時） 時，會顯示此視窗**檢視** > **其他 Windows**  >  **資料來源**。 您可以從建立控制項繫結至基礎資料，這個視窗拖曳項目，您也可以設定資料來源，以滑鼠右鍵按一下。

![資料來源視窗](../data-tools/media/raddata-data-sources-window.png)

對於 [資料來源 **] 視窗中的每個資料類型，將項目拖曳到設計工具時都會建立一個預設控制項。 拖曳的項目之前**Zdroje dat**  視窗中，您可以變更已建立的控制項。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

## <a name="tasks-involved-in-binding-controls-to-data"></a>將控制項繫結至資料的相關工作

下表列出一些最常見的工作，您執行將控制項繫結至資料。

|工作|詳細資訊|
|----------| - |
|開啟 [資料來源 **] 視窗。|在編輯器中開啟的設計介面，然後選擇**檢視** > **Zdroje dat**。|
|將資源來源加入至專案。|[新增資料來源](../data-tools/add-new-data-sources.md)|
|設定當您從 [資料來源 **] 視窗中將項目拖曳到設計工具時建立的控制項。|[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|修改與 [資料來源 **] 視窗中之項目相關聯的控制項清單。|[將自訂控制項新增至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|建立資料繫結控制項。|[將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|繫結至物件或集合。|[Visual Studio 中的物件繫結](../data-tools/bind-objects-in-visual-studio.md)|
|篩選 UI 中顯示的資料。|[在 Windows Forms 應用程式中篩選和排序資料](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|自訂控制項的標題。|[自訂 Visual Studio 為資料繫結的控制項建立標題的方式](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Forms 資料繫結](/dotnet/framework/winforms/windows-forms-data-binding)