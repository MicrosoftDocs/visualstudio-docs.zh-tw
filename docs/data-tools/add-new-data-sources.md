---
title: 加入新的資料來源
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d88ba8b5648135d361a145dbc98a82dee6836e50
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745590"
---
# <a name="add-new-data-sources"></a>加入新的資料來源
在 Visual Studio 中的.NET 資料工具的內容中的詞彙*資料來源*指的是連接到資料存放區，並將資料公開給.NET 應用程式的.NET 物件。 Visual Studio 設計工具可以取用的資料來源，以產生拖曳和卸除的資料庫物件時，將資料繫結至表單的指令碼輸出**資料來源**視窗。 這種資料來源可以是：

-   某些類型的資料庫與相關聯的 Entity Framework 模型中的類別。

-   某些類型的資料庫與相關聯的資料集。

-   類別代表網路服務，例如 Windows Communication Foundation (WCF) 的資料服務或 REST 服務。

-   表示 SharePoint 服務的類別。

-   類別或您的方案中的集合。

> [!NOTE]
>  如果您不使用資料繫結功能，資料集、 Entity Framework 中，LINQ to SQL、 WCF、 或 SharePoint，「 資料來源 」 的概念不適用。 只要直接連接到資料庫使用 SQLCommand 物件，並直接與資料庫通訊。

 您建立和編輯資料來源使用**資料來源組態精靈**Windows Form 或 Windows Presentation Foundation 應用程式中。 Entity framework，先建立實體類別，並選取，以啟動精靈**專案** > **加入新資料來源**（本文稍後將詳細說明）。

 ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)

 建立資料來源之後，它會出現在**資料來源**工具視窗 (Shift + Alt + D 或**檢視** > **其他視窗** >  **資料來源**)。 您可以拖曳資料來源從**資料來源**視窗拖曳至表單的設計介面或控制項。 這會導致產生的未定案程式碼，會顯示使用者在資料存放區的來源資料的程式碼。 下圖顯示資料集拖曳至 Windows form 已卸除。 如果您選擇 F5 對應用程式時，基礎資料庫中的資料會出現在表單的控制項。

 ![資料來源的拖曳操作](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>資料庫或資料庫檔案的資料來源

### <a name="dataset"></a>資料集
 若要建立資料集做為資料來源，執行**資料來源組態精靈**(**專案** > **加入新資料來源**)，然後選擇  **資料庫**資料來源類型。 遵循提示來指定新的或現有的資料庫連接或資料庫檔案。

### <a name="entity-classes"></a>實體類別
 若要建立 Entity Framework 模型做為資料來源，第一次執行**實體資料模型精靈**建立實體類別 (**專案** > **加入新項目** >  **ADO.NET 實體資料模型**)。

 ![新的 Entity Framework 模型專案項目](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

 選擇您想要產生模型所用的方法。

 ![實體資料模型精靈](../data-tools/media/raddata-entity-data-model-wizard.png)

 加入模型當做資料來源。 所產生的類別會出現在**資料來源組態精靈**當您選擇**物件**類別目錄。

 ![實體類別與資料來源組態精靈](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>服務的資料來源
 若要從服務中建立資料來源，請執行**資料來源組態精靈**選擇**服務**資料來源類型。 這是其實只是捷徑**加入服務參考**對話方塊中，您也可以以滑鼠右鍵按一下專案中的存取**方案總管 中**，然後選取**加入服務參考**.

 當您從服務中建立資料來源時，Visual Studio 加入服務參考加入專案。 Visual Studio 也會建立於服務所傳回的物件相對應的 proxy 物件。 比方說，傳回的資料集的服務都會在您的專案做為資料集;傳回特定型別以您的專案做為類型傳回服務。

 您可以從下列類型的服務來建立資料來源：

-   WCF 資料服務。 如需詳細資訊，請參閱[概觀](/dotnet/framework/data/wcf/wcf-data-services-overview)。

-   WCF 服務。 如需詳細資訊，請參閱[Windows Communication Foundation 服務和 Visual Studio 中的 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)。

-   Web 服務。

    > [!NOTE]
    >  在出現的項目**資料來源**視窗是否依存於服務傳回的資料。 某些服務可能會提供足夠的資訊如**資料來源組態精靈**來建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，沒有項目會出現在**資料來源**視窗中，當您完成精靈。 這是因為不具類型資料集不會提供結構描述，因此精靈沒有足夠的資訊來建立資料來源。

## <a name="data-source-for-an-object"></a>物件的資料來源
 您可以從任何執行中公開一個或多個公用屬性物件建立資料來源**資料來源組態精靈**，然後選取 **物件**資料來源類型。 物件的所有公用屬性會顯示在**資料來源**視窗。   如果您使用 Entity Framework，且已產生模型，這是您在其中找到將您的應用程式的資料來源的實體類別。

 在**選取資料物件**頁面上，展開樹狀結構檢視，來找出您想要繫結至的物件中的節點。 樹狀檢視中包含您的專案和組件和其他您專案所參考的專案節點。

 如果您想要繫結至組件或不會出現在樹狀檢視中的專案中，按一下**加入參考**並用**加入參考對話方塊**加入至組件或專案的參考。 加入參考之後，組件或專案加入至樹狀檢視。

> [!NOTE]
>  您可能需要建置的專案，然後物件才會出現在樹狀檢視中包含您的物件。

> [!NOTE]
>  若要支援拖放資料繫結，物件會實作<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>介面必須有預設建構函式。 否則，Visual Studio 無法具現化的資料來源物件，而且它會顯示錯誤，當您將項目拖曳至設計介面。

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 清單資料來源
 您可以從 SharePoint 清單建立資料來源，藉由執行**資料來源組態精靈**，然後選取**SharePoint**資料來源類型。 SharePoint 會將資料公開透過[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]，因此建立 SharePoint 資料來源是從服務中建立資料來源相同。 選取**SharePoint**中的項目**資料來源組態精靈**開啟**加入服務參考**對話方塊，連接到 SharePoint 資料服務藉由指向 SharePoint 伺服器。  這需要 SharePoint SDK。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)