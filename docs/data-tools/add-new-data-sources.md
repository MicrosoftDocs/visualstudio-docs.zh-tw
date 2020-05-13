---
title: 新增新資料來源
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302249"
---
# <a name="add-new-data-sources"></a>新增新資料來源

在 Visual Studio 中的 .NET 資料工具的上下文中，術語*資料來源*是指連接到資料存儲並使資料可供 .NET 應用程式使用. Visual Studio 設計人員可以使用資料來源的輸出來生成樣板代碼，在從**資料來源**視窗中拖放資料庫物件時將資料繫結到表單。 此類資料來源可以是：

- 實體框架模型中與某種資料庫關聯的類。

- 與某種資料庫關聯的資料集。

- 表示網路服務（如 Windows 通信基礎 （WCF） 資料服務或 REST 服務）的類。

- 表示 SharePoint 服務的類。

- 解決方案中的類或集合。

> [!NOTE]
> 如果您不使用資料繫結功能、資料集、實體框架、LINQ 到 SQL、WCF 或 SharePoint，"資料來源"的概念不適用。 只需使用 SQLCommand 物件直接連接到資料庫，並直接與資料庫通信即可。

通過使用 Windows 表單或 Windows 演示文稿基礎應用程式中的**資料來源設定精靈**創建和編輯資料來源。 對於實體框架，首先創建實體類，然後通過選擇 **"專案** > **添加新資料來源**"啟動嚮導（本文稍後將對此進行更詳細的介紹）。

![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>資料來源視窗

創建資料來源後，它將顯示在 **"資料來源"** 工具視窗中。

> [!TIP]
> 要打開**資料來源**視窗，請確保專案處於打開狀態，然後按**Shift**+**Alt**+**D**或選擇 **"查看** > **其他 Windows** > **資料來源**"。

您可以將資料來源從**資料來源**視窗拖動到表單設計介面或控制項上。 這將導致生成顯示資料存儲資料的樣板代碼。

下圖顯示了已下降到 Windows 表單的資料集。 如果在應用程式上選擇**F5，** 則基礎資料庫的資料將顯示在表單的控制項中。

![資料來源拖動操作](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>資料庫或資料庫檔案的資料來源

您可以創建資料集或實體框架模型，用作資料庫或資料庫檔案的資料來源。

### <a name="dataset"></a>資料集

要將資料集創建為數據源，請通過選擇 **"專案** > **添加新資料來源**"來運行**資料來源設定精靈**。 選擇**資料庫**資料來源類型，然後按照提示指定新的或現有的資料庫連接或資料庫檔案。

### <a name="entity-classes"></a>實體類別

要將實體框架模型創建為數據源，請進行：

1. 運行**實體資料模型嚮導**以創建實體類。 選擇**專案** > **ADO.NET** > **實體資料模型**添加新項。

   ![新實體框架模型專案項](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. 選擇要生成模型的方法。

   ![實體資料模型精靈](../data-tools/media/raddata-entity-data-model-wizard.png)

1. 將模型添加為數據源。 當您選擇 **"物件**"類別時，生成的類將顯示在**資料來源設定精靈**中。

   ![具有實體類的資料來源設定精靈](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>服務的資料來源

要從服務創建資料來源，請運行**資料來源設定精靈**並選擇**服務**資料來源類型。 這只是 **"添加服務參考"** 對話方塊的快捷方式，您也可以通過按右鍵**解決方案資源管理器**中的專案並選擇 **"添加服務引用**"來訪問該對話方塊。

從服務創建資料來源時，Visual Studio 會向專案添加服務引用。 Visual Studio 還會創建與服務返回的物件對應的代理物件。 例如，返回資料集的服務在專案中表示為資料集;因此，在專案中，返回資料集的服務將表示為資料集。返回特定類型的服務在專案中表示為返回的類型。

可以從以下類型的服務創建資料來源：

- [WCF 資料服務](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF 服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web 服務

    > [!NOTE]
    > "**資料來源**"視窗中顯示的專案取決於服務返回的資料。 部分服務所提供的資訊可能不足，無法供 [資料來源組態精靈]**** 建立可繫結的物件。 例如，如果服務返回未鍵入的資料集，則完成嚮導時，"**資料來源**"視窗中不會顯示任何項。 這是因為未鍵入的資料集不提供架構，因此嚮導沒有足夠的資訊來創建資料來源。

## <a name="data-source-for-an-object"></a>物件的資料來源

您可以通過運行**資料來源設定精靈**，然後選擇**物件**資料來源類型，從公開一個或多個公共屬性的任何物件創建資料來源。 物件的所有公共屬性都顯示在 **"資料來源"** 視窗中。 如果使用實體框架並生成了模型，則在此處可以找到作為應用程式的資料來源的實體類。

在 **"選擇資料物件"** 頁上，展開樹狀檢視中的節點以找到要綁定的物件。 樹狀檢視包含專案以及專案引用的程式集和其他專案的節點。

如果要綁定到程式集或專案中未顯示在樹狀檢視中的物件，請按一下"**添加參考**"並使用 **"增加參考"對話方塊**添加對程式集或專案的引用。 增加參考後，程式集或專案將添加到樹狀檢視中。

> [!NOTE]
> 在物件顯示在樹狀檢視中之前，您可能需要生成包含物件的專案。

> [!NOTE]
> 要支援拖放資料繫結，實現<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>介面的物件必須具有預設建構函式。 否則，Visual Studio 無法具現化資料來源物件，並且在將專案拖動到設計介面時將顯示錯誤。

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 清單的資料來源

您可以通過運行**資料來源設定精靈**並選擇**SharePoint**資料來源類型，從 SharePoint 清單中創建資料來源。 SharePoint 通過 WCF 資料服務公開資料，因此創建 SharePoint 資料來源與從服務創建資料來源相同。 在**資料來源設定精靈**中選擇**SharePoint**項將打開 **"添加服務參考"** 對話方塊，通過指向 SharePoint 伺服器連接到 SharePoint 資料服務。 這需要 SharePoint SDK。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
