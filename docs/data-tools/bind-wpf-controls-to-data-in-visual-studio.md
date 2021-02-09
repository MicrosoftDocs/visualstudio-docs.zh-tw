---
title: 將 WPF 控制項系結至資料-第1部分
description: 將 WPF 控制項系結至資料。 若要建立這些資料繫結控制項，請將專案從 [資料來源] 視窗拖曳至 Visual Studio 的 WPF 設計工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 137d8970ebfc70dcf102fa70d7bcf18d81677535
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859264"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>將 WPF 控制項繫結至 Visual Studio 中的資料

您可以透過將資料繫結至 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 控制項，對應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，您可以將專案從 [ **資料來源** ] 視窗拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] Visual Studio 中的。 本主題描述可用來建立資料繫結 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 應用程式的一些最常用工作、工具和類別。

如需有關如何在 Visual Studio 中建立資料繫結控制項的一般資訊，請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 如需資料系結的詳細資訊 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] ，請參閱資料系結 [總覽](/dotnet/desktop-wpf/data/data-binding-overview)。

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>將 WPF 控制項繫結至資料的工作

下表列出可透過從 [資料來源] 視窗將項目拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] 所完成的工作。

|Task|詳細資訊|
|----------| - |
|建立新的資料繫結控制項。<br /><br /> 將現有控制項繫結至資料。|[將 WPF 控制項繫結至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|建立可顯示父子關係中相關資料的控制項：當使用者選取某個控制項中的父資料記錄時，另一個控制項會顯示選取之記錄的相關子資料。|[在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)|
|建立「查閱資料表」，其根據某個資料表中的外部索引鍵欄位值，顯示另一個資料表的資訊。|[在 WPF 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|將控制項繫結至資料庫中的圖片。|[從資料庫將控制項繫結至圖片](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>有效置放目標

[資料來源] 視窗中的項目，只能拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] 中的有效置放目標。 有效置放目標有兩種：容器和控制項。 容器是通常會包含控制項的使用者介面項目。 例如，格線是容器，視窗也是容器。

## <a name="generated-xaml-and-code"></a>產生的 XAML 和程式碼

當您從 [ **資料來源** ] 視窗將專案拖曳至時 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] ，Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會產生，以定義新的資料繫結控制項 (或將現有控制項系結至資料來源) 。 針對某些資料來源，Visual Studio 也會在程式碼後端檔案中產生程式碼，以將資料填入資料來源。

下表列出 Visual Studio 在 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] [ **資料來源** ] 視窗中為每個資料來源類型所產生的和程式碼。

| 資料來源 | 產生可將控制項繫結至資料來源的 XAML | 產生可將資料填入資料來源的程式碼 |
| - | - | - |
| 資料集 | 是 | 是 |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | 是 | 是 |
| 服務 | 是 | 否 |
| Object | 是 | 否 |

### <a name="datasets"></a>資料集

當您從 [ **資料來源** ] 視窗將資料表或資料行拖曳至設計工具時，Visual Studio 會產生，以執行 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 下列動作：

- 將資料集或新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示資料集中的資料。

- 建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，XAML 會將控制項繫結至項目。 如果您將專案拖曳至容器，XAML 會建立針對拖曳專案所選取的控制項，並將控制項系結至專案。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

Visual Studio 也會對程式碼後置檔案進行下列變更：

- 針對包含控制項的 <xref:System.Windows.FrameworkElement.Loaded> 項目，建立 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件處理常式。 事件處理常式會將資料填入資料表，從容器的資源擷取 <xref:System.Windows.Data.CollectionViewSource>，然後讓第一個資料項目成為目前的項目。 如果 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式已經存在，Visual Studio 會將此程式碼加入至現有的事件處理常式。

### <a name="entity-data-models"></a>實體資料模型

當您將實體或實體屬性從 [ **資料來源** ] 視窗拖曳至設計工具時，Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會產生，以執行下列動作：

- 將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示實體中的資料。

- 建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會將控制項繫結至項目。 如果您將專案拖曳至容器，則 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會建立針對拖曳專案所選取的控制項，並將控制項系結至專案。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

Visual Studio 也會對程式碼後置檔案進行下列變更：

- 加入新方法，其針對您拖曳至設計工具的實體 (或包含拖曳至設計工具之屬性的實體)，傳回查詢。 新方法的名稱 `Get<EntityName>Query` 是，其中 `\<EntityName>` 是實體的名稱。

- 針對包含控制項的 <xref:System.Windows.FrameworkElement.Loaded> 項目，建立 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件處理常式。 事件處理常式會呼叫 `Get<EntityName>Query` 方法，以將資料填入實體， <xref:System.Windows.Data.CollectionViewSource> 從容器的資源抓取，然後讓第一個資料項目成為目前的專案。 如果 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式已經存在，Visual Studio 會將此程式碼加入至現有的事件處理常式。

### <a name="services"></a>服務

當您將服務物件或屬性從 [ **資料來源** ] 視窗拖曳至設計工具時，Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會產生，以建立資料繫結控制項 (或將現有控制項系結至物件或屬性) 。 不過，Visual Studio 不會產生以資料填滿 proxy 服務物件的程式碼。 您必須自行撰寫此程式碼。 如需示範如何進行此動作的範例，請參閱將 [WPF 控制項系結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。

Visual Studio 會產生執行下列工作的 XAML：

- 將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示服務所傳回之物件中的資料。

- 建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會將控制項繫結至項目。 如果您將專案拖曳至容器，則 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會建立針對拖曳專案所選取的控制項，並將控制項系結至專案。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

### <a name="objects"></a>物件

當您將物件或屬性從 [ **資料來源** ] 視窗拖曳至設計工具時，Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會產生，以建立資料繫結控制項 (或將現有控制項系結至物件或屬性) 。 不過，Visual Studio 不會產生程式碼來填滿具有資料的物件。 您必須自行撰寫此程式碼。

> [!NOTE]
> 自訂類別必須是公用的，而且預設會有不含參數的函式。 它們不能是其語法中有 "dot" 的嵌套類別。 如需詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)。

Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會產生，以執行下列動作：

- 將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示物件中的資料。

- 建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，XAML 會將控制項繫結至項目。 如果您將專案拖曳至容器，XAML 會建立針對拖曳專案所選取的控制項，並將控制項系結至專案。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
