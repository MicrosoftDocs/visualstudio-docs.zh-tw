---
title: 封裝專案專案中的 & 部署資訊
description: 使用功能屬性、功能接收器、專案輸出參考和安全控制項實體，在 SharePoint 專案專案中新增封裝和部署資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f73d8727fb960cf519d368d928aa20cae38ae1a9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970473"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>提供專案專案中的封裝和部署資訊
  中的所有 SharePoint 專案專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 都有屬性，可讓您在專案部署至 SharePoint 時，用來提供額外的資料。 這些屬性如下所示：

- 功能屬性

- 功能接收器

- 專案輸出參考

- 安全控制項項目

  這些屬性會出現在 [ **屬性** ] 視窗中。

## <a name="feature-properties"></a>功能屬性
 您可以使用 [ **功能屬性** ] 屬性來指定功能所使用的資料。 功能屬性資料是一組值， (儲存為索引鍵/值組，) 在部署至 SharePoint 時包含的功能。 部署功能之後，您可以在程式碼中存取屬性值。

 當您將功能屬性值新增至專案專案時，此值會在專案功能的資訊清單中加入為專案。 例如，在商務資料連線 (BDC) 模型專案中，ModelFileName 功能屬性會顯示為：

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 設定功能屬性值之後，它會新增為專案 *.spdata* 檔案中的 FeatureProperty 元素。 如需有關存取 SharePoint 中屬性的詳細資訊，請參閱 [SPFeaturePropertyCollection 類別](/previous-versions/office/sharepoint-server/ms461895(v=office.15))。

 所有專案專案的相同功能屬性值都會合並在功能資訊清單中。 但是，如果有兩個不同的專案專案指定具有不相符值的相同功能屬性索引鍵，就會發生驗證錯誤。

 若要將功能屬性直接加入功能 *檔 (的功能)* 中，請呼叫 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 物件模型方法 <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> 。 如果您使用此方法，請注意，在功能屬性中加入相同功能屬性值的相同規則也適用于直接新增至功能檔的屬性。

## <a name="feature-receiver"></a>功能接收器
 功能接收器是在特定事件發生于專案專案的包含功能時，所執行的程式碼。 例如，您可以定義在安裝、啟動或升級功能時執行的功能接收器。 新增功能接收器的其中一種方式，是將它直接新增至功能，如 [逐步解說：新增功能事件接收器](../sharepoint/walkthrough-add-feature-event-receivers.md)中所述。 另一種方式是在 **功能接收器** 屬性中參考功能接收器類別的名稱和元件。

### <a name="direct-method"></a>直接方法
 當您直接將功能接收器新增至功能時，會在方案總管的 **功能** 節點下放置程式碼檔案。 當您建立 SharePoint 方案時，程式碼會編譯成元件並部署到 SharePoint。 根據預設，功能屬性 **接收器元件** 和 **接收者類別** 會參考類別名稱和元件。

### <a name="reference-method"></a>Reference 方法
 新增功能接收器的另一種方式是使用專案專案的 [ **功能接收者** ] 屬性來參考功能接收器元件。 [功能接收者] 屬性值具有兩個子屬性： **元件** 和 **類別名稱**。 元件必須使用其完整的「強式」名稱，而類別名稱必須是完整的類型名稱。 如需詳細資訊，請參閱[強式名稱的組件](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100))。 將方案部署到 SharePoint 之後，此功能會使用參考的功能接收器來處理功能事件。

 在方案建立期間，功能和其專案中的功能接收器屬性值會合並在一起，以在 SharePoint 方案 (*.wsp*) 檔的功能資訊清單中，設定 feature 專案的 ReceiverAssembly 和 ReceiverClass 屬性。 因此，如果同時指定專案專案和功能的元件和類別名稱屬性值，則專案專案和功能屬性值必須相符。 如果值不相符，您將會收到驗證錯誤。 如果您想要讓專案專案參考功能接收器元件，而不是其功能所用的元件，請將它移至另一個功能。

 如果您參考尚未存在於伺服器上的功能接收器元件，則您也必須在封裝中包含元件檔案本身。不 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會為您新增。 當您部署此功能時，元件檔會複製到 [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] SharePoint 實體目錄中的系統或 Bin 資料夾中。 如需詳細資訊，請參閱 how to： [如何：加入和移除其他元件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。

 如需功能接收器的詳細資訊，請參閱 [功能事件接收器](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) 和 [功能事件](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14))。

## <a name="project-output-references"></a>專案輸出參考
 專案輸出參考屬性指定您的專案專案需要執行的相依性，例如元件。 例如，假設您的方案有一個 BDC 專案和一個類別專案。 如果 BDC 專案相依于類別專案所輸出的元件，您可以參考 BDC 專案的 [專案輸出參考] 屬性中的元件。 封裝 BDC 專案時，相依元件會包含在封裝中。

 專案輸出參考通常是元件，但在某些情況下 (例如 Silverlight 專案) 可以是其他檔案類型。

 如需詳細資訊，請參閱 [如何：加入專案輸出參考](../sharepoint/how-to-add-a-project-output-reference.md)。

## <a name="safe-control-entries"></a>安全控制項專案
 SharePoint 提供安全性機制，稱為安全控制項專案，可將不受信任的使用者存取限制為特定控制項。 根據設計，SharePoint 可讓不受信任的使用者上傳和建立 SharePoint 伺服器上的 ASPX 頁面。 為了防止這些使用者將 unsafe 程式碼新增至 ASPX 頁面，SharePoint 會限制其對 *安全控制項* 的存取。 安全控制項是指定為安全的 ASPX 控制項和 Web 元件，可供您網站上的任何使用者使用。 如需詳細資訊，請參閱 [步驟4：將您的網頁元件新增至安全控制項清單](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12))。

 中的每個 SharePoint 專案專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 都有一個稱為 **安全控制項** 專案的屬性，這些專案具有兩個布林子屬性： **安全** 且 **安全地針對腳本**。 [安全] 屬性會指定未受信任的使用者是否能存取控制項。 [安全地針對腳本] 屬性會指定不受信任的使用者是否可以查看和變更控制項的屬性。

 安全控制項專案是以元件為基礎參考。 您可以藉由在專案專案的 [ **安全控制項** 專案] 屬性中輸入安全控制項專案，將安全控制項專案加入專案的元件中。 但是，當您將其他元件加入封裝時，您也可以透過 **封裝設計** 工具中的 [ **Advanced** ] 索引標籤，將安全的控制項專案加入專案的元件中。 如需詳細資訊，請參閱 [如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md) 或 [將 Web 元件元件註冊為安全控制項](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))。

### <a name="xml-entries-for-safe-controls"></a>安全控制項的 XML 專案
 當您將安全控制項專案加入至專案專案或專案的元件時，參考會以下列格式寫入封裝資訊清單中：

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
