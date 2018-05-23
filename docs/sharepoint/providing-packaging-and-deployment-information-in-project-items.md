---
title: 提供封裝和專案項目中的部署資訊 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0c12c01566011ed93d83cd9ecc0dd417edd0b1b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Providing Packaging and Deployment Information in Project Items
  中的所有 SharePoint 專案項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]有的屬性，您可以使用專案部署至 SharePoint 時，提供額外的資料。 這些屬性如下所示：  
  
-   功能屬性  
  
-   功能接收器  
  
-   專案輸出參考  
  
-   安全控制項項目  
  
 這些屬性會出現在**屬性**視窗。  
  
## <a name="feature-properties"></a>功能屬性  
 使用**功能屬性**屬性以指定的功能使用的資料。 功能屬性資料是一組值 （儲存為索引鍵/值組），將部署至 SharePoint 時，會包含與功能。 部署功能之後，您可以在程式碼中存取屬性值。  
  
 功能屬性值加入專案項目時的值會加入的項目功能的資訊清單中的項目。 商務資料連線 (BDC) 模型專案中，例如 ModelFileName 功能屬性會顯示為：  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 設定功能屬性值之後，它會成為在專案的.spdata 檔案 FeatureProperty 項目。 如需存取 SharePoint 中的屬性資訊，請參閱[SPFeaturePropertyCollection 類別](http://go.microsoft.com/fwlink/?LinkId=177391)。  
  
 從專案的所有項目相同的功能屬性值會合併在一起的功能資訊清單中。 不過，如果兩個不同的專案項目指定相同的功能屬性索引鍵不相符的值，就會發生驗證錯誤。  
  
 功能屬性直接新增到功能檔案 (*.feature)，呼叫[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 物件模型方法<xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>。 如果您使用此方法時，請注意有關功能屬性中加入相同的功能屬性值相同的規則也適用於直接加到功能檔案的屬性。  
  
## <a name="feature-receiver"></a>功能接收器  
 功能接收器是專案項目發生特定事件時執行程式碼所含的功能。 例如，您可以定義功能安裝、 啟動，或升級時執行的功能接收器。 其中一種方式將它直接新增到一項功能中所述的功能接收器是[逐步解說： 新增功能事件接收器](../sharepoint/walkthrough-add-feature-event-receivers.md)。 另一個方法為參考功能接收器類別名稱和組件中的**功能接收器**屬性。  
  
### <a name="direct-method"></a>直接方法  
 當您新增功能接收器的一項功能直接時，程式碼檔案位於**功能**方案總管 中的節點。 當您建置 SharePoint 解決方案時，程式碼會編譯成組件，並將部署到 SharePoint。 根據預設，功能屬性**接收器組件**和**接收器類別**參考的類別名稱和組件。  
  
### <a name="reference-method"></a>Reference 方法  
 若要加入功能接收器的另一個方法是使用**功能接收器**屬性參考功能接收器組件的專案項目。 功能接收器的屬性值具有兩個：**組件**和**類別名稱**。 組件必須使用其完整、 「 強式 」 的名稱和類別名稱必須是完整類型名稱。 如需詳細資訊，請參閱[強式名稱的組件](http://go.microsoft.com/fwlink/?LinkID=169573)。 將方案部署至 SharePoint 之後, 功能會使用被參考的功能接收器處理功能的事件。  
  
 在方案建置時，功能接收器中的屬性值的功能和其專案合併在一起設定 ReceiverAssembly 和 ReceiverClass 屬性功能項目的 SharePoint 方案 (.wsp) 檔案的功能資訊清單中。 因此，如果同時指定組件和類別名稱屬性值的專案項目和功能，必須符合專案項目和功能屬性值。 如果值不相符，您會收到驗證錯誤。 如果您的專案項目參考功能接收器組件，卻不使用其功能，請將它移到另一項功能。  
  
 如果您參考功能接收器組件尚未在伺服器上，您也必須包含組件檔案本身封裝中;[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不會為您新增。 當您部署此功能時，組件檔會複製到其中一個系統[!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)]或在 SharePoint 實體目錄的 Bin 資料夾。 如需詳細資訊，請參閱 < 如何：[如何： 加入和移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 如需功能接收器的詳細資訊，請參閱[功能事件接收器](http://go.microsoft.com/fwlink/?LinkID=169574)和[功能事件](http://go.microsoft.com/fwlink/?LinkID=169575)。  
  
## <a name="project-output-references"></a>專案輸出參考  
 專案輸出參考屬性指定的相依性，例如您的專案項目需要執行的組件。 例如，假設您的方案有 BDC 專案和類別專案。 如果 BDC 專案輸出的類別專案的組件有相依性，您可以參考 BDC 專案的專案輸出參考屬性中的組件。 當封裝 BDC 專案時，相依組件會包含在封裝中。  
  
 專案輸出參考通常是組件，但在某些情況下 （例如 Silverlight 專案） 可以是其他檔案類型。  
  
 如需詳細資訊，請參閱[如何： 加入專案輸出參考](../sharepoint/how-to-add-a-project-output-reference.md)。  
  
## <a name="safe-control-entries"></a>安全控制項項目  
 SharePoint 所提供的安全性機制，稱為安全控制項項目，來限制特定的控制項，不受信任使用者的存取權。 根據設計，SharePoint 可讓不信任的使用者上傳並在 SharePoint 伺服器上建立 ASPX 頁面。 若要避免這些使用者將不安全的程式碼加入至 ASPX 網頁，SharePoint 會限制其存取權*安全控制項*。 安全控制項 ASPX 控制項和網頁組件指定為安全而且，可以由您的網站上的任何使用者。 如需詳細資訊，請參閱[步驟 4： 將您的 Web 組件加入至安全的控制項清單](http://go.microsoft.com/fwlink/?LinkID=171014)。  
  
 在每個 SharePoint 專案項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有名**安全控制項項目**具有兩個布林子屬性：**安全**和**防止指令碼**。 [安全] 屬性會指定未受信任的使用者是否能存取控制項。 防止指令碼屬性指定了不受信任的使用者是否可以檢視和變更控制項的屬性。  
  
 安全控制項項目會參考組件為基礎。 將安全控制項項目加入至專案的組件的專案項目中輸入它們**安全控制項項目**屬性。 不過，您也可以加入安全控制項項目至專案的組件透過**進階**索引標籤中**封裝設計工具**將其他組件加入封裝。 如需詳細資訊，請參閱[如何： 為安全控制項的標記控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)或[Web 組件登錄成安全控制](http://go.microsoft.com/fwlink/?LinkID=171013)。  
  
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
  