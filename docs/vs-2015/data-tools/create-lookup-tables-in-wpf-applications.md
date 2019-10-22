---
title: 在 WPF 應用程式中建立查閱資料表 |Microsoft Docs
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657417"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>在 WPF 應用程式中建立查閱資料表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「詞彙*查閱資料表*」（有時稱為「*查閱*系結」）描述的控制項會根據另一個資料表中的外鍵欄位值，顯示一個資料表的資訊。 您可以在 [**資料來源**] 視窗中，將父資料表或物件的主要節點拖曳到已系結至相關子資料工作表中之資料行或屬性的控制項，以建立查閱資料表。

 例如，假設 sales 資料庫中的 `Orders` 資料表。 @No__t_0 資料表中的每筆記錄都包含 `CustomerID`，以指出哪個客戶下訂單。 @No__t_0 是指向 `Customers` 資料表中之客戶記錄的外鍵。 當您從 [`Orders`] 資料表顯示訂單清單時，您可能會想要顯示實際的客戶名稱，而不是 [`CustomerID`]。 由於客戶名稱位於 `Customers` 資料表中，因此您必須建立查閱資料表以顯示客戶名稱。 查閱資料表會使用 `Orders` 記錄中的 `CustomerID` 值來流覽關聯性，並傳回客戶名稱。

## <a name="to-create-a-lookup-table"></a>若要建立查閱資料表

1. 將下列其中一種資料來源類型新增至您的專案：

    - 資料集或實體資料模型。

    - WCF 資料服務、WCF 服務或 Web 服務。 如需詳細資訊，請參閱[如何：連接至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。

    - 物件。 如需詳細資訊，請參閱[如何：連接至物件中的資料](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b)。

    > [!NOTE]
    > 您必須先將兩個相關的資料表或物件當做專案的資料來源存在，才能建立查閱資料表。

2. 開啟**WPF 設計**工具，並確定設計工具組含的容器是 [**資料來源**] 視窗中專案的有效放置目標。

     如需有效放置目標的詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

3. 按一下 [資料] 功能表上的 [顯示資料來源]，以開啟 [資料來源] 視窗。

4. 展開 [**資料來源**] 視窗中的節點，直到您看到父資料表或物件以及相關的子資料工作表或物件為止。

    > [!NOTE]
    > 相關的子資料工作表或物件是在父資料表或物件下顯示為可擴充子節點的節點。

5. 按一下子節點的下拉式功能表，然後選取 [**詳細資料**]。

6. 展開子節點。

7. 在子節點底下，按一下與子系和父資料相關聯之專案的下拉式功能表。 （在上述範例中，這是 [ **CustomerID** ] 節點）。選取下列其中一種支援查閱系結的控制項類型：

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > 如果**ListBox**或**ListView**控制項沒有出現在清單中，您可以將這些控制項加入清單中。 如需相關資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

    - 從 <xref:System.Windows.Controls.Primitives.Selector> 衍生的任何自訂控制項。

        > [!NOTE]
        > 如需如何將自訂控制項加入至 [**資料來源**] 視窗中的專案之控制項清單的詳細資訊，請參閱[將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

8. 將子節點從 [**資料來源**] 視窗拖曳至 WPF 設計工具中的容器。 （在上述範例中，子節點是 [ **Orders** ] 節點）。

     Visual Studio 會產生 XAML，針對您拖曳的每個專案建立新的資料繫結控制項。 XAML 也會將子資料工作表或物件的新 <xref:System.Windows.Data.CollectionViewSource> 加入至放置目標的資源。 針對某些資料來源，Visual Studio 也會產生程式碼，以將資料載入至資料表或物件。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

9. 將父節點從 [**資料來源**] 視窗拖曳至您稍早建立的查閱繫結控制項。 （在上述範例中，父節點是 [ **Customers** ] 節點）。

     Visual Studio 會在控制項上設定一些屬性，以設定查閱系結。 下表列出 Visual Studio 修改的屬性。 如有需要，您可以在 XAML 或 [**屬性**] 視窗中變更這些屬性。

    |屬性|設定說明|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|這個屬性會指定用來取得控制項中所顯示之資料的集合或系結。 Visual Studio 會將此屬性設定為您拖曳至控制項之父資料的 <xref:System.Windows.Data.CollectionViewSource>。|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|這個屬性會指定顯示在控制項中的資料項目路徑。 Visual Studio 在具有字串資料類型的主鍵之後，將此屬性設定為父資料中的第一個資料行或屬性。<br /><br /> 如果您想要在父資料中顯示不同的資料行或屬性，請將這個屬性變更為不同屬性的路徑。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 會將此屬性系結至您拖曳至設計工具之子資料的資料行或屬性。 這是父資料的外鍵。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 將此屬性設定為父資料之外鍵之子資料的資料行或屬性路徑。|

## <a name="see-also"></a>請參閱
 [將 wpf 控制項系結至中的資料 Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)將[wpf 控制項系結至](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [wpf 應用程式中 Visual Studio 顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)的資料[逐步解說：在 wpf 應用程式中顯示相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
