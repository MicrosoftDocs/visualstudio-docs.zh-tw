---
title: 當地語系化 SharePoint 方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b653efc0cce8d8fb2b3e28b8e6c61e6371b4f6e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837352"
---
# <a name="localize-sharepoint-solutions"></a>當地語系化 SharePoint 方案

  準備您的應用程式，以便它們可全球使用的處理程序稱為 「 當地語系化 」。 當地語系化轉譯特定文化特性的資源。 如需詳細資訊，請參閱 < [Globalizing and Localizing Applications](../ide/globalizing-and-localizing-applications.md)。 本主題提供有關如何當地語系化 SharePoint 方案的概觀。  
  
 若要當地語系化方案，您可以從程式碼中移除硬式編碼的字串，並它們抽出資源檔。 資源檔[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-架構檔案 *.resx*延伸模組。 資源檔包含在解決方案中使用的字串翻譯的版本。 如需詳細資訊，請參閱 <<c0> [ 應用程式中的資源](http://go.microsoft.com/fwlink/?LinkID=155844)。  
  
> [!NOTE]  
>  加入 SharePoint 方案資源檔中只有字串資源。 雖然資源編輯器可讓您將非字串資源，但是非字串資源不會部署到 SharePoint。  
  
## <a name="resource-files"></a>資源檔
 有三種類型的資源檔： 預設、 語言中性和特定語言。  
  
|資源檔案類型|描述|  
|------------------------|-----------------|  
|預設|也稱為後援資源，預設資源檔包含預設文化特性，例如英文版的當地語系化字串。 如果找不到指定語言的當地語系化的資源檔，使用。 預設資源沒有個別的檔案，它們儲存在主應用程式組件。|  
|非語言相關|資源檔，其中包含當地語系化的語言，但不是特定文化特性的字串。 例如，"fr"代表法文。|  
|特定語言|資源檔，其中包含當地語系化的語言及文化特性的字串。 例如，"FR-CA"加拿大法文。|  
  
 如需詳細資訊，請參閱 <<c0> [ 階層式組織當地語系化的資源](http://go.microsoft.com/fwlink/?LinkId=178360)。  
  
 若要指定預設資源檔中開發 SharePoint 專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，選擇**因語言而異 （Invariant 國家/地區）** 文化特性清單中的**加入資源**對話方塊時您加入資源檔。  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>當地語系化 Visual Studio SharePoint 方案
 當您當地語系化方案時，您應該考慮所有您的解決方案會向使用者顯示的文字資訊。 告知性訊息、 錯誤訊息和[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]字串必須進行轉譯，而且那些轉譯放置在資源檔。  
  
 資源檔中的每個字串都有唯一的識別碼。 翻譯的字串，在每個資源檔中使用相同的識別項。 比方說，如果"String1"是預設資源檔中的第一個字串的識別項，請使用相同的識別項中的特定語言資源檔的第一個字串。  
  
 有三個區域，您通常會當地語系化中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 應用程式： 功能、 ASPX 頁面標記和程式碼。 下列各節進行說明，假設您有想要當地語系化為德文和日文的 SharePoint 方案。 預設語言是英文。  
  
### <a name="localize-features"></a>當地語系化功能
 若要當地語系化功能，您必須參考已轉譯的標題和字串在當地語系化的資源檔中的運算式中取代的硬式編碼的標題和描述的功能。 您進行這項變更**功能設計工具**在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱[＜How to：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)。  
  
 若要將英文功能當地語系化為德文和日文，您必須將三個資源檔的專案項目加入專案： 分別用於英文、 德文和日文。 功能資源檔不能用來當地語系化 ASPX 標記或程式碼;需要為其個別的資源檔。  
  
 您建立功能資源檔之後，將翻譯的字串加入它們。 存取當地語系化的字串，以下列格式的運算式：  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 中的功能資源[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]始終稱為 「 資源。 如果您選取的語言而異，則文化特性以外的語言[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]新增至資源檔名稱。 例如，如果您新增的語言而異 （預設值） 的功能資源檔時，它會呼叫*Resources.resx*。 如果您新增的語言特有的功能資源選取日文 （日本） 文化特性時，檔案稱為*則 Resources.ja-jp.resx*。 功能資源檔名稱會自動指派，且無法變更。  
  
 功能資源的範圍是功能新增至本機。 若要建立可由方案中的任何功能或項目檔案的資源，請新增**全域資源檔案**專案項目，而非功能資源檔。 **全域資源檔**專案項目位於**2010年**下的資料夾**SharePoint**中**加入新項目** 對話方塊。 全域資源檔部署至 SharePoint 根資料夾的 \Resources 資料夾。  
  
### <a name="localize-aspx-page-markup"></a>當地語系化 ASPX 頁面標記
 若要當地語系化[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面，專案中加入三個資源檔的專案項目： 分別用於英文、 德文和日文。 如果您不需要當地語系化程式碼除了標記以外，您可以改為加入全域資源檔案。  
  
 提供的預設語言資源檔案的名稱。 提供當地語系化的資源檔相同的名稱附加有語言特定文化特性[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，*為 MyAppResources.de-DE.resx*德文並*而日文*日文。  
  
 設定**部署類型**屬性的每個資源檔**AppGlobalResource**。 這會導致要部署至 App_GlobalResources 資料夾，可用於所有的 ASPX 頁面和控制項，在方案中的資源檔。 App_GlobalResources 資料夾位於 C:\inetpub\wwwroot\wss\VirtualDirectories\\< 連接埠號碼\>\App_GlobalResources。  
  
> [!NOTE]  
>  如果您使用非全域資源檔，請將它們移到專案項目資料夾，若要啟用的部署類型屬性和其他 SharePoint 特定屬性。  
  
 ASPX 標記資源檔也可用來當地語系化程式碼。 如果您使用的資源来當地語系化 ASPX 標記除了程式碼，將 [建置動作] 屬性設定每個檔案做為內嵌資源，以將資源編譯成附屬組件。 不過，如果您只當地語系化標記會使用資源檔，您可以防止將檔案編譯成主應用程式組件的內容 （選擇性） 變更 建置動作。  
  
 在 ASPX 頁面和控制項標記中的所有硬式編碼屬性字串取代運算式格式如下：  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如:   
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 文字型的 ASPX，使用運算式中以下列格式的內容：  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如:   
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 如需詳細資訊，請參閱[＜How to：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)。  
  
### <a name="localize-code"></a>當地語系化程式碼
 除了當地語系化 「 功能 」 字串和[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]標記中，您還必須當地語系化的訊息字串和出現在您方案的程式碼中的錯誤字串。 當地語系化的告知性及錯誤訊息包含在附屬組件。 附屬組件包含字串時，會對使用者顯示，例如[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]文字和輸出訊息類似例外狀況。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用標準的.NET Framework 中樞和支點模型。 中樞或主程式組件包含預設語言資源。 該輪輻或附屬組件，包含語言特定資源。 如需詳細資訊，請參閱[封裝和部署資源](http://go.microsoft.com/fwlink/?LinkId=179280)。 附屬組件編譯自資源 (*.resx*) 檔案。 當您將語言特定資源檔新增至您的專案和方案套件時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將資源檔編譯成附屬組件名為 *.resources.dll {專案名稱}*。  
  
 如同 ASPX 標記，可以將個別的資源檔的專案項目新增至您的專案，以當地語系化 SharePoint 應用程式程式碼其中一個預設語言，一個用於每個當地語系化語言。 不過，如前所述，如果您已經有用於當地語系化 ASPX 標記的資源檔，您可以重複使用它們來當地語系化程式碼。 如果您需要建立資源檔，提供的預設語言資源檔案加上您所選擇的名稱 *.resx*延伸模組。 相同的名稱附加有語言特定文化特性名稱的當地語系化的資源檔[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 每個資源檔的 [建置動作] 屬性設為內嵌資源，以啟用附屬資源組件的建立。  
  
 若要建立附屬組件，建置專案，並接著將檔案新增為額外的組件，透過**進階**索引標籤**封裝設計工具**。 當加入組件，在前面加上文化特性[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]資料夾的位置路徑，例如*DE-DE\\{專案項目名稱}.resources.dll*。 這可讓套件包含具有相同名稱的檔案。  
  
 在您的程式碼中硬式編碼字串取代呼叫<xref:System.Web.HttpContext.GetGlobalResourceObject%2A>方法使用下列語法：  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 如需詳細資訊，請參閱[＜How to：當地語系化程式碼](../sharepoint/how-to-localize-code.md)。  
  
#### <a name="web-part-code-localization"></a>Web 組件程式碼當地語系化
 Web 組件包含自訂屬性編輯器 功能，包括使用硬式編碼的字串，例如 WebDisplayName、 Category 和 WebDescription 的程式碼屬性。 若要取代這些屬性的字串值，建立個別的類別衍生自屬性的類別。 在這些類別中，設定該屬性的屬性。 將屬性取決於基底類別。 例如，WebDisplayName 屬性屬性為 DisplayNameValue，而 WebDescription 屬性屬性為 DescriptionValue。  
  
 在衍生類別中，參考的字串 ID 的資源檔和 ResourceManager 物件來取得當地語系化的字串 id。 此值傳回至屬性編輯器。  
  
## <a name="see-also"></a>另請參閱
 [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)   
 [如何：加入資源檔](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
