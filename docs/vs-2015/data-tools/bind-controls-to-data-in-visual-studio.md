---
title: 將控制項系結至資料
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
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673040"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>將控制項繫結至 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以透過將資料繫結至控制項，對應用程式的使用者顯示資料。 您可以從 [**資料來源**] 視窗將專案拖曳至設計介面，或 Visual Studio 中介面上的控制項，以建立這些資料繫結控制項。

 這個主題描述可用來建立資料繫結控制項的資料來源。 此外，也描述與資料繫結相關的一些一般工作。 如需如何建立資料繫結控制項的詳細資訊，請參閱將[Windows Forms 控制項系結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)，並[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="data-sources"></a>資料來源
 在資料系結的內容中，資料來源代表可以系結至您的使用者介面之記憶體中的資料。 實際上，資料來源可以是 Entity Framework 類別、資料集、封裝在 .NET proxy 物件中的服務端點、LINQ to SQL 類別，或任何 .NET 物件或集合。 有些資料來源可讓您從 [資料來源] 視窗拖曳項目，以建立資料繫結控制項，有些資料來源則否。 下表顯示支援的資料來源。

|資料來源|**Windows Form 設計工具**的拖放功能支援|**WPF 設計工具**的拖放功能支援|**Silverlight Designer** 的拖放功能支援|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|資料集|[是]|[是]|否|
|實體資料模型|是<sup>1</sup>|[是]|[是]|
|LINQ to SQL 類別|否<sup>2</sup>|否<sup>2</sup>|否<sup>2</sup>|
|服務 (包括 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]、WCF 服務和 Web 服務)|[是]|[是]|[是]|
|Object|[是]|[是]|[是]|
|SharePoint|[是]|[是]|[是]|

 1. 使用**實體資料模型**wizard 來產生模型，然後將這些物件拖曳至設計工具。

 2. LINQ to SQL 類別不會出現在 [資料來源] 視窗中。 不過，您可以根據 LINQ to SQL 類別加入新的物件資料來源，然後將這些物件拖曳至設計工具，來建立資料繫結控制項。 如需詳細資訊，請參閱[逐步解說：建立 LINQ to SQL 類別（O-R 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)。

## <a name="data-sources-window"></a>資料來源視窗
 資料來源可在 [資料來源] 視窗中以項目形式用於專案。 當表單設計介面是專案中的使用中視窗時，可以看到此視窗，或可從 [ **View** ] 功能表存取。 您可以從這個視窗拖曳專案，以建立系結至基礎資料的控制項，而且您也可以用滑鼠右鍵按一下來設定資料來源。

 ![[資料來源] 視窗](../data-tools/media/raddata-data-sources-window.png "raddata 資料來源視窗")

 對於 [資料來源] 視窗中的每個資料類型，將項目拖曳到設計工具時都會建立一個預設控制項。 在您從 [**資料來源**] 視窗拖曳專案之前，您可以變更將建立的控制項。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

## <a name="tasks-involved-in-binding-controls-to-data"></a>將控制項繫結至資料的相關工作
 下表列出將控制項系結至資料時，您可以執行的一些最常見工作。

|工作|詳細資訊|
|----------|----------------------|
|開啟 [資料來源] 視窗。|在編輯器中開啟設計介面，然後選擇 [ **View**  > **Data 來源**]。|
|將資源來源新增至專案。|[新增資料來源](../data-tools/add-new-data-sources.md)|
|設定當您從 [資料來源] 視窗中將項目拖曳到設計工具時建立的控制項。|[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|修改與 [資料來源] 視窗中之項目相關聯的控制項清單。|[將自訂控制項新增至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|建立資料繫結控制項。|[將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|系結至物件或集合。|[Visual Studio 中的物件繫結](../data-tools/bind-objects-in-visual-studio.md)|
|篩選出現在 UI 中的資料。|[在 Windows Forms 應用程式中篩選和排序資料](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|自訂控制項的標題。|[自訂 Visual Studio 為資料繫結的控制項建立標題的方式](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>請參閱
 [適用于 .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms 資料](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)系結的 Visual Studio 資料工具
