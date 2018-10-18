---
title: 逐步解說： 顯示 Windows Form 上的資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f623f639458a9f5c9c055b5d6de384f6fd39cad1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201197"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>逐步解說：顯示 Windows Form 上的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在應用程式的開發過程中，最常見的一個情節就是在 Windows 應用程式的表單上顯示資料。 您可以在表單上顯示資料，項目從[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至表單。 這個逐步解說會建立簡單表單，以顯示來自數個個別控制項中單一資料表的資料。 此範例使用 Northwind 範例資料庫中的 `Customers` 資料表。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新**Windows 應用程式**專案。  
  
-   建立和設定與資料集[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。  
  
-   選取要拖曳的項目時，表單上建立的控制項**Zdroje dat**視窗。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   建立資料繫結控制項中的項目**Zdroje dat**視窗拖曳至表單。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="creating-the-windows-application"></a>建立 Windows 應用程式  
 第一個步驟是建立**Windows 應用程式**專案。  
  
#### <a name="to-create-the-new-windows-application-project"></a>建立新的 Windows 應用程式專案  
  
1.  從**檔案** 功能表中，建立新的專案。  
  
2.  將專案命名為 `DisplayingDataonaWindowsForm`。  
  
3.  選取  **Windows 應用程式**然後按一下**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     **DisplayingDataonaWindowsForm**建立專案並將其加入至**方案總管 中**。  
  
## <a name="creating-the-data-source"></a>建立資料來源  
 這個步驟會建立使用資料來源**資料來源組態精靈**根據`Customers`Northwind 範例資料庫中的資料表。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態精靈**。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在 **選擇您的資料連接**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         -或-  
  
    -   選取 **新的連線**來啟動**加入/修改連接**對話方塊...  
  
5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下**下一步**。  
  
6.  按一下 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
7.  依序展開**資料表**上的節點**選擇您的資料庫物件**頁面。  
  
8.  選取 **客戶**資料表，然後按一下**完成**。  
  
     **NorthwindDataSet**新增至您的專案並**客戶**資料表會出現在**Zdroje dat**視窗。  
  
## <a name="setting-the-controls-to-be-created"></a>設定要建立的控制項  
 此逐步解說中，資料會在**詳細資料**其中資料會顯示在個別控制項的版面配置。 (替代方法是預設值**格線**版面配置資料會顯示在<xref:System.Windows.Forms.DataGridView>控制項。)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>在資料來源視窗中設定項目的卸除類型  
  
1.  依序展開**客戶**中的節點**Zdroje dat**視窗。  
  
2.  卸除類型變更**客戶**資料表**詳細資料**選取**詳細資料**上的下拉式清單從**客戶**節點。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
3.  變更**CustomerID**藉由選取標籤資料行的卸除類型**標籤**上的控制項清單**CustomerID**節點。  
  
## <a name="creating-the-form"></a>建立表單  
 建立資料繫結控制項中的項目**Zdroje dat**視窗拖曳至表單。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項  
  
-   主**客戶**從節點**Zdroje dat**視窗拖曳至表單。  
  
     會在表單上顯示具有描述性標籤的資料繫結控制項，以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>)。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
## <a name="testing-the-application"></a>測試應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   按 F5。  
  
-   使用 <xref:System.Windows.Forms.BindingNavigator> 控制項，以巡覽記錄。  
  
## <a name="next-steps"></a>後續步驟  
 根據應用程式的需求，在建立資料繫結程序 Windows Form 後，可能會有幾個想要執行的步驟。 一些您可以加強這個逐步解說的部分包括：  
  
-   將搜尋功能加入至表單。 如需詳細資訊，請參閱 <<c0> [ 如何： 將參數化查詢加入至 Windows Forms 應用程式](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)。  
  
-   加入將更新送回資料庫的功能。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 將資料儲存至資料庫 （單一資料表）](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d)。  
  
-   新增`Orders`資料表選取資料集**以精靈設定資料集**內在**資料來源**視窗。 然後您可以加入顯示相關的資料的拖曳的控制項**訂單** 節點 (下面的**傳真**內的資料行**客戶**資料表) 拖曳至表單。 如需詳細資訊，請參閱[如何：在 Windows Forms 應用程式中顯示相關的資料](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)