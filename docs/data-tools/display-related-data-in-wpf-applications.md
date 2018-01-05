---
title: "WPF 應用程式中顯示相關的資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5313269a4575cb41ebe6e8b9cedb5ca02d49b493
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="display-related-data-in-wpf-applications"></a>WPF 應用程式中顯示相關的資料
在某些應用程式，您可以使用來自多個資料表或實體的父子式關聯性中彼此有關聯的資料。 例如，您可能想要顯示一個方格，其中會顯示從客戶`Customers`資料表。 當使用者選取特定的客戶時，另一個方格會顯示該客戶的相關訂單`Orders`資料表。

您可以建立資料繫結控制項顯示相關的資料的項目從**資料來源**WPF 設計工具的視窗。

## <a name="to-create-controls-that-display-related-records"></a>若要建立顯示相關的記錄的控制項

1. 在**資料**功能表上，按一下 **顯示資料來源**開啟**資料來源**視窗。

2. 按一下**加入新資料來源**，並完成**資料來源組態**精靈。

3. 開啟 WPF 設計工具中，並確定在設計工具包含的項目中的有效置放目標的容器**資料來源**視窗。

     如需有效置放目標的詳細資訊，請參閱[繫結 WPF 控制項加入 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

4. 在**資料來源**視窗中，展開節點，表示父資料表或關聯性中的物件。 父資料表或物件是一對多關聯性的 「 一 」 端上。

5. 拖曳父節點 （或任何個別的項目父節點中） 從**資料來源**視窗拖曳至設計工具中的有效置放目標。

     Visual Studio 會產生 XAML，會建立新的資料繫結控制項，針對您拖曳每個項目。 XAML 也會加入新<xref:System.Windows.Data.CollectionViewSource>父資料表或物件的拖放目標資源。 對於某些資料來源，Visual Studio 也會產生程式碼，以將資料載入至父資料表或物件。 如需詳細資訊，請參閱[繫結 WPF 控制項加入 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

6. 在**資料來源**視窗中，找出相關的子系資料表或物件。 相關的子系資料表和物件會顯示為資料的父節點的清單底部的可展開節點。

7. 將子節點 （或任何子節點中的個別項目） 從拖曳**資料來源**視窗拖曳至設計工具中的有效置放目標。

     Visual Studio 會產生針對每一個您拖曳的項目建立新的資料繫結控制項的 XAML。 XAML 也會加入新<xref:System.Windows.Data.CollectionViewSource>子資料表或物件的拖放目標資源。 這個新<xref:System.Windows.Data.CollectionViewSource>繫結至您剛才拖曳至設計工具的物件之父資料表的屬性。 對於某些資料來源，Visual Studio 也會產生程式碼，以將資料載入至子資料表或物件。

     下圖示範相關**訂單**資料表**客戶**資料表中的資料集在**資料來源**視窗。

     ![顯示關聯的資料來源視窗](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>另請參閱
[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[在 WPF 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)