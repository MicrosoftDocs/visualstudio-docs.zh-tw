---
title: 在 WPF 應用程式中建立查閱資料表
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1631f1b93f79c21914f990620f7e0047c301163f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567815"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>在 WPF 應用程式中建立查閱資料表

詞彙*查閱資料表*(有時也稱為*查閱繫結*) 描述會顯示資訊從一個資料表，根據另一個資料表中的外部索引鍵欄位值的控制項。 您可以藉由拖曳父資料表的主要節點建立查閱資料表或物件**Zdroje dat**視窗拖曳至已繫結至資料行或屬性相關的子資料表中的控制項。

例如，假設資料表的`Orders`銷售資料庫中。 在每一筆記錄`Orders`資料表包含`CustomerID`，指出哪些客戶下過訂單。 `CustomerID`中的客戶記錄會指向為外部索引鍵`Customers`資料表。 當您顯示一份訂單`Orders`資料表中，您可能想要顯示實際的客戶名稱，而不是`CustomerID`。 因為客戶名稱是在`Customers`資料表中，您需要建立查閱資料表，以顯示客戶名稱。 查閱資料表中使用`CustomerID`中的值`Orders`記錄巡覽關聯性，並傳回客戶名稱。

## <a name="to-create-a-lookup-table"></a>若要建立查閱資料表

1. 將下列一種類型的相關資料的資料來源新增至您的專案：

    - 資料集或實體資料模型。

    - WCF 資料服務，WCF 服務或 web 服務。 如需詳細資訊，請參閱[如何：連線至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。

    - 物件。 如需詳細資訊，請參閱 <<c0> [ 繫結至 Visual Studio 中的物件](bind-objects-in-visual-studio.md)。

    > [!NOTE]
    > 您可以建立查閱資料表之前，必須存在兩個相關的資料表或物件當做專案資料來源。

2. 開啟**WPF 設計工具**，並確定設計工具會包含有效的置放目標中的項目容器**Zdroje dat**視窗。

     如需有關有效置放目標的詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

3. 按一下 [資料] 功能表上的 [顯示資料來源]，以開啟 [資料來源] 視窗。

4. 展開中的節點**Zdroje dat**  視窗中，直到您可以看到父資料表或物件和關聯的子資料表或物件。

    > [!NOTE]
    > 會顯示為在父資料表或物件的可展開的子節點的節點是相關的子資料表或物件。

5. 按一下下拉式選單，子節點，然後選取**詳細資料**。

6. 展開子節點。

7. 子節點底下，按一下下拉式功能表與相關的子系和父資料的項目。 (在上述範例中，這是**CustomerID**節點。)選取下列一種類型的支援查閱繫結的控制項：

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > 如果**ListBox**或是**ListView**控制項不會出現在清單中，您可以將這些控制項新增至清單。 如需資訊，請參閱[設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

    - 任何自訂控制項衍生自<xref:System.Windows.Controls.Primitives.Selector>。

        > [!NOTE]
        > 如何加入自訂控制項的控制項清單以您可以選取中的項目**資料來源** 視窗中，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

8. 從 [子] 節點拖曳**Zdroje dat**視窗拖曳至 WPF 設計工具中的容器。 (在上述範例中，子節點是**訂單**節點。)

     Visual Studio 會產生每個您所拖曳的項目建立新的資料繫結控制項的 XAML。 XAML 也會加入新<xref:System.Windows.Data.CollectionViewSource>子資料表或物件的置放目標的資源。 對於某些資料來源，Visual Studio 也會產生程式碼，以將資料載入資料表或物件。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

9. 將從父節點拖曳**Zdroje dat**視窗拖曳至您稍早建立的查閱繫結控制項。 (在上述範例中，是父節點**客戶**節點)。

     Visual Studio 會將設定查閱繫結控制項上的某些屬性。 下表列出 Visual Studio 會修改的屬性。 如果有必要，您可以變更這些屬性在 XAML 中或**屬性**視窗。

    |屬性|設定說明|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|此屬性會指定集合或用來取得的資料，會顯示在控制項中的繫結。 Visual Studio 會將此屬性設定為<xref:System.Windows.Data.CollectionViewSource>針對您拖曳至控制項的父資料。|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|此屬性會指定在控制項中顯示之資料項目的路徑。 Visual Studio 設定此屬性的第一個資料行或屬性在父資料中，主索引鍵具有字串資料類型之後。<br /><br /> 如果您想要在父資料顯示不同的資料行或屬性，變更此屬性的不同屬性的路徑。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 這個屬性繫結至資料行或您拖曳到設計工具的子資料的屬性。 這是父資料的外部索引鍵。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 會設定這個屬性的路徑資料行或屬性的父資料的外部索引鍵的子資料。|

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)
- [逐步解說：在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)