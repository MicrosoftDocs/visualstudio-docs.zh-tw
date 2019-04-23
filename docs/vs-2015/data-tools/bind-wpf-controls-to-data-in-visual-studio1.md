---
title: 將 WPF 控制項繫結至資料 |Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d34b973043cf5147fa28c08a37945610a7030268
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663007"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>將 WPF 控制項繫結至 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以透過將資料繫結至 [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] 控制項，對應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，您可以將項目從**資料來源**視窗拖曳至[!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 本主題描述可用來建立資料繫結 [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] 應用程式的一些最常用工作、工具和類別。

 如需如何建立資料繫結控制項中的一般資訊[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請參閱 <<c2> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 如需 [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] 資料繫結的詳細資訊，請參閱[資料繫結概觀](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)。

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>將 WPF 控制項繫結至資料的工作
 下表列出可透過從 [資料來源] 視窗將項目拖曳至 [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] 所完成的工作。

|工作|詳細資訊|
|----------|----------------------|
|建立新的資料繫結控制項。<br /><br /> 將現有控制項繫結至資料。|[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)[繫結 WPF 控制項新增至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|建立可顯示父子關係中相關資料的控制項：當使用者選取某個控制項中的父資料記錄時，另一個控制項會顯示選取之記錄的相關子資料。|[在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)|
|建立「查閱資料表」，其根據某個資料表中的外部索引鍵欄位值，顯示另一個資料表的資訊。|[在 WPF 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|將控制項繫結至資料庫中的圖片。|[從資料庫將控制項繫結至圖片](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>有效置放目標
 [資料來源] 視窗中的項目，只能拖曳至 [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] 中的有效置放目標。 有效置放目標有兩種：容器和控制項。 容器是通常會包含控制項的使用者介面項目。 例如，格線是容器，視窗也是容器。

## <a name="generated-xaml-and-code"></a>產生的 XAML 和程式碼
 當您拖曳的項目**資料來源** 視窗來[!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]，定義新的資料繫結控制項 （或將現有控制項繫結至資料來源）。 對於某些資料來源，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會在程式碼後置檔案中產生可將資料填入資料來源的程式碼。

 下表列出[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]和程式碼[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會為每一種資料來源中產生**Zdroje dat**視窗。

|資料來源|產生可將控制項繫結至資料來源的 XAML|產生可將資料填入資料來源的程式碼|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|資料集|是|是|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|是|是|
|服務|是|否|
|Object|是|否|

### <a name="datasets"></a>資料集
 當您將資料表或資料行**資料來源**設計工具中，視窗[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]，會執行下列：

- 將資料集或新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示資料集中的資料。

- 建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，XAML 會將控制項繫結至項目。 如果您將項目拖曳至容器時，XAML 會建立為拖曳的項目，所選取的控制項和它的項目繫結的控制項。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會對程式碼後置檔案進行下列變更：

- 針對包含控制項的 <xref:System.Windows.FrameworkElement.Loaded> 項目，建立 [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] 事件處理常式。 事件處理常式會將資料填入資料表，從容器的資源擷取 <xref:System.Windows.Data.CollectionViewSource>，然後讓第一個資料項目成為目前的項目。 如果<xref:System.Windows.FrameworkElement.Loaded>事件處理常式已經存在，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]將此程式碼加入至現有的事件處理常式。

### <a name="entity-data-models"></a>實體資料模型
 當您拖曳實體或實體屬性從**資料來源**設計工具中，視窗[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]，會執行下列：

- 將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示實體中的資料。

- 建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 會將控制項繫結至項目。 如果您將項目拖曳到容器中，[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]建立控制項，已選取拖曳的項目，且它將控制項繫結至項目。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

  Visual Studio 也會對程式碼後置檔案進行下列變更：

- 加入新方法，其針對您拖曳至設計工具的實體 (或包含拖曳至設計工具之屬性的實體)，傳回查詢。 新的方法有名稱為 Get*EntityName*查詢，其中*EntityName*是實體的名稱。

- 針對包含控制項的 <xref:System.Windows.FrameworkElement.Loaded> 項目，建立 [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] 事件處理常式。 事件處理常式會呼叫 Get*EntityName*Query 方法將擷取的資料中填入實體<xref:System.Windows.Data.CollectionViewSource>從容器的資源，然後讓第一個資料項目的目前項目。 如果<xref:System.Windows.FrameworkElement.Loaded>事件處理常式已經存在，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]將此程式碼加入至現有的事件處理常式。

### <a name="services"></a>服務
 當您將服務物件或屬性從**資料來源**設計工具中，視窗[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]建立資料繫結控制項 （或將現有控制項繫結至物件或屬性）。 不過，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 不會產生可將資料填入 Proxy 服務物件的程式碼。 您必須自行撰寫此程式碼。 如需示範如何執行這項操作的範例，請參閱 <<c0> [ 繫結 WPF 控制項新增至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。

 Visual Studio 會產生執行下列工作的 XAML：

-   將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示服務所傳回之物件中的資料。

-   建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 會將控制項繫結至項目。 如果您將項目拖曳到容器中，[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]建立控制項，已選取拖曳的項目，且它將控制項繫結至項目。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

### <a name="objects"></a>物件
 當您將物件或屬性從**資料來源**設計工具中，視窗[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]建立資料繫結控制項 （或將現有控制項繫結至物件或屬性）。 不過，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 不會產生可將資料填入物件的程式碼。 您必須自行撰寫此程式碼。

> [!NOTE]
>  自訂類別必須是公用的和，根據預設，具有不含參數的建構函式。 它們不能有 「 點 」，其語法中的巢狀的類別。 如需詳細資訊，請參閱 < [XAML 和自訂類別，如 WPF](http://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a)。

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]，會進行下列作業：

-   將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。 <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示物件中的資料。

-   建立控制項的資料繫結。 如果您將項目拖曳至設計工具中的現有控制項，XAML 會將控制項繫結至項目。 如果您將項目拖曳至容器時，XAML 會建立為拖曳的項目，所選取的控制項和它的項目繫結的控制項。 控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。

## <a name="see-also"></a>另請參閱
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
