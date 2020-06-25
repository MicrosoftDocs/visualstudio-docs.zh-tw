---
title: 在 WPF 應用程式中建立查閱資料表
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7485c63d358bc6f6fe7030e589fbdf7286ded3fd
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282614"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>在 WPF 應用程式中建立查閱資料表

「詞彙*查閱資料表*」（有時稱為「*查閱*系結」）描述的控制項會根據另一個資料表中的外鍵欄位值，顯示一個資料表的資訊。 您可以在 [**資料來源**] 視窗中，將父資料表或物件的主要節點拖曳到已系結至相關子資料工作表中之資料行或屬性的控制項，以建立查閱資料表。

例如，請考慮 `Orders` sales 資料庫中的資料表。 資料表中的每筆記錄 `Orders` `CustomerID` 都包含，以指出哪個客戶下訂單。 `CustomerID`是指向資料表中客戶記錄的外鍵 `Customers` 。 當您顯示資料表中的訂單清單時 `Orders` ，您可能會想要顯示實際的客戶名稱，而不是 `CustomerID` 。 由於客戶名稱是在資料表中 `Customers` ，因此您必須建立查閱資料表來顯示客戶名稱。 查閱資料表使用 `CustomerID` 記錄中的值 `Orders` 來導覽關聯性，並傳回客戶名稱。

## <a name="to-create-a-lookup-table"></a>若要建立查閱資料表

1. 將下列其中一種資料來源類型新增至您的專案：

    - 資料集或實體資料模型。

    - WCF 資料服務、WCF 服務或 web 服務。 如需詳細資訊，請參閱[如何：連接至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。

    - 物件。 如需詳細資訊，請參閱系結[至 Visual Studio 中的物件](bind-objects-in-visual-studio.md)。

    > [!NOTE]
    > 您必須先將兩個相關的資料表或物件當做專案的資料來源存在，才能建立查閱資料表。

2. 開啟**WPF 設計**工具，並確定設計工具組含的容器是 [**資料來源**] 視窗中專案的有效放置目標。

     如需有效放置目標的詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

3. 按一下 [資料]**** 功能表上的 [顯示資料來源]****，以開啟 [資料來源]**** 視窗。

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

    - 衍生自的任何自訂控制項 <xref:System.Windows.Controls.Primitives.Selector> 。

        > [!NOTE]
        > 如需如何將自訂控制項加入至 [**資料來源**] 視窗中的專案之控制項清單的詳細資訊，請參閱[將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

8. 將子節點從 [**資料來源**] 視窗拖曳至 WPF 設計工具中的容器。 （在上述範例中，子節點是 [ **Orders** ] 節點）。

     Visual Studio 會產生 XAML，針對您拖曳的每個專案建立新的資料繫結控制項。 XAML 也會將 <xref:System.Windows.Data.CollectionViewSource> 子資料工作表或物件的新新增至放置目標的資源。 針對某些資料來源，Visual Studio 也會產生程式碼，以將資料載入至資料表或物件。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

9. 將父節點從 [**資料來源**] 視窗拖曳至您稍早建立的查閱繫結控制項。 （在上述範例中，父節點是 [ **Customers** ] 節點）。

     Visual Studio 會在控制項上設定一些屬性，以設定查閱系結。 下表列出 Visual Studio 修改的屬性。 如有需要，您可以在 XAML 或 [**屬性**] 視窗中變更這些屬性。

    |屬性|設定說明|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|這個屬性會指定用來取得控制項中所顯示之資料的集合或系結。 Visual Studio 將此屬性設定為 <xref:System.Windows.Data.CollectionViewSource> 您拖曳至控制項之父資料的。|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|這個屬性會指定顯示在控制項中的資料項目路徑。 Visual Studio 在具有字串資料類型的主鍵之後，將此屬性設定為父資料中的第一個資料行或屬性。<br /><br /> 如果您想要在父資料中顯示不同的資料行或屬性，請將這個屬性變更為不同屬性的路徑。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 會將此屬性系結至您拖曳至設計工具之子資料的資料行或屬性。 這是父資料的外鍵。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 將此屬性設定為父資料之外鍵之子資料的資料行或屬性路徑。|

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)
- [逐步解說：在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)
