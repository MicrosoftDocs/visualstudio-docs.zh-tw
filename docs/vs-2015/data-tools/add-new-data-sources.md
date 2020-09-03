---
title: 加入新的資料來源 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85c07ad7995bc614df4b988bb17fa8977452b5d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673069"
---
# <a name="add-new-data-sources"></a>新增新資料來源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 的 .NET data tools 內容中，「 *資料來源* 」一詞是指連接到資料存放區的 .net 物件，並將資料公開至 .net 應用程式。 當您從 [ **資料來源** ] 視窗中拖放資料庫物件時，Visual Studio 設計工具可以取用資料來源的輸出，以產生將資料系結至表單的未定案程式碼。 這種資料來源可以是：

- Entity Framework 模型中與某種資料庫相關聯的類別。

- 與某一種資料庫相關聯的資料集。

- 代表網路服務的類別，例如 Windows Communication Foundation (WCF) 資料服務或 REST 服務。

- 表示 SharePoint 服務的類別。

- 方案中的類別或集合。

> [!NOTE]
> 如果您不是使用資料系結功能、資料集、Entity Framework、LINQ to SQL、WCF 或 SharePoint，則「資料來源」的概念並不適用。 只要使用 SQLCommand 物件直接連接到資料庫，就可以直接與資料庫進行通訊。

 您可以使用 Windows Forms 或 Windows Presentation Foundation 應用程式中的 [ **資料來源設定]** 來建立和編輯資料來源。 針對 Entity Framework，請先建立您的實體類別，然後選取 [**專案**  >  **加入新的資料 (源**] 來啟動精靈，此文章稍後會詳細說明) 。

 ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png "資料來源組態精靈")

 在您建立資料來源之後，它會出現在 [**資料來源**] 工具視窗中 (Shift + Alt + D 或**View**  >  **Other Windows**  >  **資料來源**) 。 您可以將資料來源從 [ **資料來源** ] 視窗拖曳至表單設計介面或控制項。 這會導致產生未定案的程式碼，此程式碼會顯示源自資料存放區給使用者的資料。 下圖顯示已放入 Windows form 上的資料集。 如果您在應用程式上選取 [F5]，則基礎資料庫中的資料會出現在表單的控制項中。

 ![資料來源拖曳操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata 資料來源拖曳操作")

## <a name="data-source-for-a-database-or-a-database-file"></a>資料庫或資料庫檔案的資料來源

### <a name="dataset"></a>資料集
 若要建立資料集做為資料來源，請執行 [**資料來源設定]** ， (**Project**  >  **加入新的資料**源) ，然後選擇**資料庫**資料來源類型。 遵循提示來指定新的或現有的資料庫連接，或資料庫檔案。

### <a name="entity-classes"></a>實體類別
 若要建立 Entity Framework 模型做為資料來源，請先執行**實體資料模型 Wizard** ，建立實體類別 (**Project**新增  >  **專案**  >  **ADO.NET 實體資料模型**) 。

 ![新的 Entity Framework 模型專案專案](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata 新的 Entity Framework 模型專案專案")

 選擇您想要用來產生模型的方法。

 ![實體資料模型精靈](../data-tools/media/raddata-entity-data-model-wizard.png "raddata 實體資料模型 Wizard")

 將模型新增為數據源。 當您選擇 [**物件**] 類別時，所產生的類別會出現在 [**資料來源設定]** 中。

 ![具有實體類別的資料來源設定 Wizard](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "具有實體類別的 raddata 資料來源設定 Wizard")

## <a name="data-source-for-a-service"></a>服務的資料來源
 若要從服務建立資料來源，請執行 [ **資料來源設定] 嚮導** ，然後選擇 [ **服務** ] 資料來源類型。 這其實只是 **加入服務參考** 對話方塊的快捷方式，您也可以在 **方案總管** 中的專案上按一下滑鼠右鍵，然後選取 [ **加入服務參考**]，來存取這個對話方塊。

 當您從服務建立資料來源時，Visual Studio 會將服務參考加入至您的專案。 Visual Studio 也會建立 proxy 物件，這些物件會對應至服務傳回的物件。 例如，傳回資料集的服務會在您的專案中表示為資料集;傳回特定類型的服務會在您的專案中表示為傳回的型別。

 您可以從下列類型的服務建立資料來源：

- WCF 資料服務。 如需詳細資訊，請參閱[概觀](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)。

- WCF data services。 如需詳細資訊，請參閱 [Visual Studio 中的 Windows Communication Foundation 服務和 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)。

- Web 服務。

    > [!NOTE]
    > 出現在 [ **資料來源** ] 視窗中的專案，取決於服務所傳回的資料。 部分服務所提供的資訊可能不足，無法供 [資料來源組態精靈]**** 建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，當您完成嚮導時，[ **資料來源** ] 視窗中不會出現任何專案。 這是因為不具類型的資料集不會提供架構，因此 wizard 沒有足夠的資訊來建立資料來源。

## <a name="data-source-for-an-object"></a>物件的資料來源
 您可以執行 [ **資料來源設定向導]** ，然後選取 [ **物件** 資料來源類型]，從任何公開一個或多個公用屬性的物件建立資料來源。 物件的所有公用屬性都會顯示在 [ **資料來源** ] 視窗中。   如果您使用 Entity Framework 並已產生模型，您可以在這裡找到將作為應用程式資料來源的實體類別。

 在 [ **選取資料物件** ] 頁面上，展開樹狀檢視中的節點，以找出您想要系結的物件。 樹狀檢視包含專案的節點，以及專案所參考的元件和其他專案的節點。

 如果您想要系結至元件或專案中未出現在樹狀檢視中的物件，請按一下 [ **加入參考** ]，然後使用 [ **加入參考] 對話方塊** ，將參考加入至元件或專案。 加入參考之後，元件或專案就會加入至樹狀檢視。

> [!NOTE]
> 您可能需要先建立包含物件的專案，物件才會出現在樹狀檢視中。

> [!NOTE]
> 若要支援拖放資料系結，執行或介面的物件 <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> 必須有預設的函式。 否則，Visual Studio 無法將資料來源物件具現化，而且當您將專案拖曳至設計介面時，它將會顯示錯誤。

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 清單的資料來源
 您可以執行 [ **資料來源設定向導]** ，然後選取 [ **sharepoint** 資料來源類型]，從 sharepoint 清單建立資料來源。 SharePoint 會透過公開資料 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] ，因此建立 SharePoint 資料來源與從服務建立資料來源的方式相同。 在 [**資料來源設定]** 中選取**SharePoint**專案，會開啟 [**加入服務參考**] 對話方塊，您可以在其中指向 SharePoint 伺服器，以連接到 sharepoint 資料服務。  這需要 SharePoint SDK。

## <a name="see-also"></a>另請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
