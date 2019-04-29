---
title: 在 WPF 應用程式中顯示相關資料
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da6f276e714c816ea9b3c1b735ad50f31ffdc3c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567053"
---
# <a name="display-related-data-in-wpf-applications"></a>在 WPF 應用程式中顯示相關資料

在某些應用程式中，您可能想要使用來自多個資料表或在父子式關聯性彼此相關的實體的資料。 例如，您可能想要顯示一個方格，其中會顯示從客戶`Customers`資料表。 當使用者選取特定的客戶時，另一部的方格會顯示該客戶的相關訂單`Orders`資料表。

您可以建立資料繫結控制項，顯示相關的資料的項目從**Zdroje dat**至 WPF 設計工具 視窗。

## <a name="to-create-controls-that-display-related-records"></a>若要建立顯示相關的記錄控制項

1. 按一下 [資料] 功能表上的 [顯示資料來源]，以開啟 [資料來源] 視窗。

2. 按一下 [新增資料來源]，並完成 [資料來源組態精靈]。

3. 開啟 WPF 設計工具中，並確定設計工具會包含有效的置放目標中的項目容器**Zdroje dat**視窗。

     如需有關有效置放目標的詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

4. 在 [ **Zdroje dat** ] 視窗中，展開代表父資料表的節點或關聯性中的物件。 物件的父資料表是一對多關聯性的 「 一 」 端上。

5. 將父節點 （或任何個別的項目父節點中） 從拖曳**Zdroje dat**視窗拖曳至設計工具中的有效置放目標。

     Visual Studio 會產生 XAML 會建立新的資料繫結控制項，您將每個項目。 XAML 也會加入新<xref:System.Windows.Data.CollectionViewSource>父資料表或物件的置放目標的資源。 對於某些資料來源，Visual Studio 也會產生程式碼，以將資料載入至父資料表或物件。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

6. 在 [ **Zdroje dat** ] 視窗中，找出相關的子資料表或物件。 相關的子資料表和物件會顯示為可展開節點底部的父節點的清單中的資料。

7. 將子節點 （或任何子節點中的個別項目） 從拖曳**Zdroje dat**視窗拖曳至設計工具中的有效置放目標。

     Visual Studio 會產生每個您所拖曳的項目建立新的資料繫結控制項的 XAML。 XAML 也會加入新<xref:System.Windows.Data.CollectionViewSource>子資料表或物件的置放目標的資源。 這個新<xref:System.Windows.Data.CollectionViewSource>繫結至您剛拖曳至設計工具的物件之父資料表的屬性。 對於某些資料來源，Visual Studio 也會產生程式碼，以將資料載入至子資料表或物件。

     下圖示範相關**訂單**的資料表**客戶**資料表中的資料集**Zdroje dat**視窗。

     ![顯示關聯的資料來源視窗](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [在 WPF 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)