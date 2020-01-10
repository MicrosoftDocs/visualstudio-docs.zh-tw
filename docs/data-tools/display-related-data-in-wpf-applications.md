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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ab1301e421f8326cf4cdda97556ecb19e394c29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586675"
---
# <a name="display-related-data-in-wpf-applications"></a>在 WPF 應用程式中顯示相關資料

在某些應用程式中，您可能會想要使用來自多個資料表或實體（在父子式關聯性中彼此相關）的資料。 例如，您可能會想要顯示一個格線，以顯示 `Customers` 資料表中的客戶。 當使用者選取特定的客戶時，另一個方格會顯示該客戶從相關 `Orders` 資料表的訂單。

您可以從 [**資料來源**] 視窗將專案拖曳至 WPF 設計工具，以建立顯示相關資料的資料繫結控制項。

## <a name="to-create-controls-that-display-related-records"></a>建立顯示相關記錄的控制項

1. 按一下 [資料] 功能表上的 [顯示資料來源]，以開啟 [資料來源] 視窗。

2. 按一下 [新增資料來源]，並完成 [資料來源組態精靈]。

3. 開啟 WPF 設計工具，並確定設計工具組含的容器是 [**資料來源**] 視窗中專案的有效放置目標。

     如需有效放置目標的詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

4. 在 [**資料來源**] 視窗中，展開代表關聯性中之父資料表或物件的節點。 父資料表或物件是在一對多關聯性的「一」端。

5. 將父節點（或父節點中的任何個別專案）從 [**資料來源**] 視窗拖曳至設計工具中有效的放置目標。

     Visual Studio 會產生 XAML，針對您拖曳的每個專案建立新的資料繫結控制項。 XAML 也會將父資料表或物件的新 <xref:System.Windows.Data.CollectionViewSource> 加入至放置目標的資源。 針對某些資料來源，Visual Studio 也會產生程式碼，將資料載入至父資料表或物件。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

6. 在 [**資料來源**] 視窗中，找出相關的子資料工作表或物件。 相關的子資料工作表和物件在父節點的資料清單底部會顯示為可擴充的節點。

7. 將子節點（或子節點中的任何個別專案）從 [**資料來源**] 視窗拖曳至設計工具中有效的放置目標。

     Visual Studio 會產生 XAML，為您所拖曳的每個專案建立新的資料繫結控制項。 XAML 也會將子資料工作表或物件的新 <xref:System.Windows.Data.CollectionViewSource> 加入至放置目標的資源。 這個新的 <xref:System.Windows.Data.CollectionViewSource> 會系結至您剛才拖曳至設計工具之父資料表或物件的屬性。 針對某些資料來源，Visual Studio 也會產生程式碼，將資料載入至子資料工作表或物件。

     下圖將示範 [**資料來源**] 視窗中資料集內 [ **Customers** ] 資料表的相關**Orders**資料表。

     ![顯示關聯的資料來源視窗](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [在 WPF 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)
