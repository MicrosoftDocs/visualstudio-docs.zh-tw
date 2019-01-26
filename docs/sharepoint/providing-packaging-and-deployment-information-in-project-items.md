---
title: 提供封裝和專案項目中的部署資訊 |Microsoft Docs
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
ms.openlocfilehash: 248bf442924ab427b41875272771d2d55708f233
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870070"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>提供專案項目中的封裝和部署資訊
  中的所有 SharePoint 專案項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]有屬性，您可以使用專案部署到 SharePoint 時，提供額外的資料。 這些屬性如下所示：  
  
- 功能屬性  
  
- 功能接收器  
  
- 專案輸出參考  
  
- 安全控制項項目  
  
  這些屬性會出現在**屬性**視窗。  
  
## <a name="feature-properties"></a>功能屬性
 使用**功能屬性**屬性以指定的功能使用的資料。 功能屬性資料是一組值 （儲存為索引鍵/值組），它會部署到 SharePoint 時，會包含的功能。 部署功能之後，您可以在程式碼中存取屬性值。  
  
 當您將功能屬性值加入專案項目時，值被加入的項目功能的資訊清單中的項目。 在商務資料連接 (BDC) 模型專案中，例如 ModelFileName 功能屬性會顯示為：  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 設定功能屬性值之後，它會新增在專案的 FeatureProperty 項目做 *.spdata*檔案。 如需存取 SharePoint 中的屬性的詳細資訊，請參閱 < [SPFeaturePropertyCollection 類別](http://go.microsoft.com/fwlink/?LinkId=177391)。  
  
 從所有的專案項目相同的功能屬性值會合併在一起的功能資訊清單中。 不過，如果兩個不同的專案項目指定相同的功能屬性索引鍵不相符的值，就會發生驗證錯誤。  
  
 功能屬性將直接加入至功能檔案 (*.feature*)，呼叫[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 物件模型方法<xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>。 如果您使用這個方法時，請注意有關在功能屬性中新增相同的功能屬性值相同的規則也適用於直接加入的功能檔案的屬性。  
  
## <a name="feature-receiver"></a>功能接收器
 功能接收器，則當專案項目中發生特定事件時執行的程式碼所含的功能。 例如，您可以定義功能安裝、 啟動，或升級時執行的功能接收器。 其中一種方式新增的功能接收器會將它直接加入一項功能，如中所述[逐步解說：新增功能事件接收器](../sharepoint/walkthrough-add-feature-event-receivers.md)。 另一個方法是參考功能接收器類別名稱和組件中的**功能接收器**屬性。  
  
### <a name="direct-method"></a>直接方法
 當您新增的功能接收器的一項直接時，有程式碼檔案位於**功能**方案總管 中的節點。 當您建置 SharePoint 方案時，程式碼會編譯成組件，並部署至 SharePoint。 根據預設，功能屬性**接收器組件**並**接收器類別**參考組件與類別名稱。  
  
### <a name="reference-method"></a>Reference 方法
 若要新增的功能接收器的另一個方法是使用**功能接收器**屬性來參考功能接收器組件的專案項目。 功能接收器屬性值具有兩個子屬性：**組件**並**類別名稱**。 組件必須使用其完整，「 強式 」 的名稱和類別名稱必須是完整類型名稱。 如需詳細資訊，請參閱[強式名稱的組件](http://go.microsoft.com/fwlink/?LinkID=169573)。 之後將解決方案部署至 SharePoint 中，功能會使用參考的功能接收器，以處理功能的事件。  
  
 在方案建置時間，此功能功能中的接收器屬性值和其專案合併在一起設定 ReceiverAssembly 和 ReceiverClass 屬性功能項目的 SharePoint 方案的功能資訊清單中 (*.wsp*) 檔案。 因此，如果同時指定專案項目和功能的組件和類別名稱的屬性值，必須符合專案項目和功能屬性值。 如果值不相符，您會收到驗證錯誤。 如果您想要的專案項目參考的功能接收器組件不是使用其功能，將它移到另一項功能。  
  
 如果您參考尚未在伺服器的功能接收器組件時，您也必須包含組件檔案本身在封裝中;[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不會為您新增。 當您部署此功能時，組件檔會複製到其中一個系統[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)]或在 SharePoint 實體目錄的 Bin 資料夾。 如需詳細資訊，請參閱 < 如何：[如何：新增和移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 如需有關功能接收器的詳細資訊，請參閱[功能事件接收器](http://go.microsoft.com/fwlink/?LinkID=169574)並[功能事件](http://go.microsoft.com/fwlink/?LinkID=169575)。  
  
## <a name="project-output-references"></a>專案輸出參考
 專案輸出參考屬性會指定為相依性，例如您的專案項目需要執行的組件。 例如，假設您的方案有 BDC 專案和類別專案。 如果 BDC 專案具有相依於組件所輸出的類別專案，您可以參考 BDC 專案的專案輸出參考屬性中的組件。 當封裝 BDC 專案時，相依的組件會包含在封裝中。  
  
 專案輸出參考通常是組件，但在某些情況下 （例如 Silverlight 專案中） 可以是其他檔案類型。  
  
 如需詳細資訊，請參閱[＜How to：加入專案輸出參考](../sharepoint/how-to-add-a-project-output-reference.md)。  
  
## <a name="safe-control-entries"></a>安全控制項項目
 SharePoint 提供安全性機制，稱為安全控制項項目，以限制至特定控制項的不受信任使用者的存取。 根據設計，SharePoint 可讓不受信任的使用者上傳，並在 SharePoint 伺服器上建立 ASPX 頁面。 若要避免這些使用者將不安全的程式碼新增至 ASPX 頁面，SharePoint 會限制其存取權*安全控制項*。 安全控制項都 ASPX 控制項和網頁組件指定為安全且可用於在您的網站上的任何使用者。 如需詳細資訊，請參閱[步驟 4:將您的 Web 組件新增至安全控制項清單](http://go.microsoft.com/fwlink/?LinkID=171014)。  
  
 在每個 SharePoint 專案項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有名**安全控制項項目**具有兩個布林子屬性：**安全**並**防止指令碼威脅**。 [安全] 屬性會指定未受信任的使用者是否能存取控制項。 防止指令碼屬性指定不受信任的使用者是否可以檢視和變更控制項的屬性。  
  
 安全控制項項目會參考組件為基礎。 將安全控制項項目新增至專案的組件的專案項目中輸入它們**安全控制項項目**屬性。 不過，您也可以將安全控制項項目加入專案的組件，透過**進階**索引標籤中**封裝設計工具**將額外的組件加入封裝。 如需詳細資訊，請參閱[＜How to：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)或是[Web 組件註冊為安全控制項](http://go.microsoft.com/fwlink/?LinkID=171013)。  
  
### <a name="xml-entries-for-safe-controls"></a>安全控制項的 XML 項目
 當專案項目或專案的組件，您會將安全控制項項目時，參考會寫入封裝資訊清單，格式如下：  
  
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
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
