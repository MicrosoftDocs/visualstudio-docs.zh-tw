---
title: "WPF 應用程式建立查閱資料表 |Microsoft 文件"
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 78322512fdc59b4ba661bca0d40d1532ac4c98e2
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF 應用程式建立查閱資料表
詞彙*查閱資料表*(有時稱為*查閱繫結*) 描述會顯示資訊從一個資料表，另一個資料表中的外部索引鍵欄位的值為基礎的控制項。 您可以透過將主要節點的父資料表中建立查閱資料表或物件存放至**資料來源**視窗拖曳至已繫結至資料行或屬性相關的子系資料表中的控制項。  
  
例如，假設資料表的`Orders`銷售資料庫中。 在每一筆記錄`Orders`資料表包含`CustomerID`指出哪位客戶下訂單。 `CustomerID`為外部索引鍵中的客戶記錄為指向`Customers`資料表。 當您顯示訂單清單`Orders`資料表中，您可能想要顯示實際客戶名稱，而不是`CustomerID`。 在客戶的名稱，所以`Customers`資料表中，您需要建立查閱資料表以顯示客戶的名稱。 查閱資料表中使用`CustomerID`值`Orders`記錄巡覽關聯性，並傳回客戶名稱。  
  
## <a name="to-create-a-lookup-table"></a>若要建立查閱資料表  
  
1.  將下列一種類型的相關資料的資料來源加入至專案：  
  
    -   資料集或實體資料模型。 
  
    -   WCF 資料服務，WCF 服務或 Web 服務。 如需詳細資訊，請參閱[如何： 連接到服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
    -   物件。 如需詳細資訊，請參閱[繫結至 Visual Studio 中的物件](bind-objects-in-visual-studio.md)。  
  
    > [!NOTE]
    >  您可以建立查閱資料表之前，必須存在兩個相關的資料表或物件做為專案的資料來源。  
  
2.  開啟**WPF 設計工具**，並確定設計工具會包含項目中的有效置放目標的容器**資料來源**視窗。  
  
     如需有效置放目標的詳細資訊，請參閱[繫結 WPF 控制項加入 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
3.  在**資料**功能表上，按一下 **顯示資料來源**開啟**資料來源**視窗。  
  
4.  展開中的節點**資料來源**視窗中，直到您可以看見父資料表或物件和關聯的子資料表或物件。  
  
    > [!NOTE]
    >  相關的子系資料表或物件是會顯示為在父資料表或物件的可展開的子節點的節點。  
  
5.  按一下子節點，而下拉式選單，然後選取**詳細資料**。  
  
6.  展開的子節點。  
  
7.  子節點下，按一下下拉式功能表與相關子和父資料的項目。 (在上述範例中，這是**CustomerID**節點。)選取下列一種類型的支援對應繫結的控制項：  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  如果**ListBox**或**ListView**控制項沒有出現在清單中，您可以將這些控制項加入至清單。 如需資訊，請參閱[設定要從資料來源視窗拖曳時建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
    -   任何自訂控制項衍生自<xref:System.Windows.Controls.Primitives.Selector>。  
  
        > [!NOTE]
        >  如何將自訂控制項加入的控制項清單您可以選取中的項目**資料來源**視窗中，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
8.  從子節點拖曳**資料來源**視窗拖曳至 WPF 設計工具中的容器。 (在上述範例中，子節點是**訂單**節點。)  
  
     Visual Studio 會產生針對每一個您拖曳的項目建立新的資料繫結控制項的 XAML。 XAML 也會加入新<xref:System.Windows.Data.CollectionViewSource>子資料表或物件的拖放目標資源。 對於某些資料來源，Visual Studio 也會產生程式碼，將資料載入資料表或物件。 如需詳細資訊，請參閱[繫結 WPF 控制項加入 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
9. 從父節點拖曳**資料來源**視窗拖曳至您稍早建立的查詢繫結控制項。 (在上述範例中，父節點是**客戶**節點)。  
  
     Visual Studio 來設定查閱繫結控制項上設定某些屬性。 下表列出 Visual Studio 會修改的屬性。 如果有必要，您可以變更這些屬性的 XAML 或**屬性**視窗。  
  
    |屬性|設定說明|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|此屬性指定的集合或用來取得的資料，會顯示在控制項中的繫結。 Visual Studio 會將此屬性設定為<xref:System.Windows.Data.CollectionViewSource>針對您拖曳至控制項的父資料。|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|此屬性指定的路徑會顯示在控制項中的資料項目。 Visual Studio 會將設定這個屬性的第一個資料行或屬性在父資料後面主索引鍵具有字串資料類型。<br /><br /> 如果您想要在父資料顯示不同的資料行或屬性，變更此屬性的不同屬性的路徑。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 會將這個屬性繫結至資料行或屬性拖曳至設計工具的子資料。 這是父資料的外部索引鍵。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 會設定這個屬性的資料行的路徑或父資料的外部索引鍵的子資料的內容。|  
  
## <a name="see-also"></a>請參閱
[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)   
[逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/display-related-data-in-wpf-applications.md)