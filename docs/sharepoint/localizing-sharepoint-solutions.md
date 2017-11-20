---
title: "當地語系化 SharePoint 方案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8186110b04e3ff56b3c6b0cad03890f3233c03d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-sharepoint-solutions"></a>當地語系化 SharePoint 方案
  準備您的應用程式，讓它們可以用於全球的過程稱為當地語系化。 當地語系化轉譯特定的文化特性的資源。 如需詳細資訊，請參閱[全球化和當地語系化應用程式](/visualstudio/ide/globalizing-and-localizing-applications)。 本主題提供有關如何當地語系化 SharePoint 方案的概觀。  
  
 若要當地語系化的方案，您從程式碼移除硬式編碼的字串和其到資源檔。 資源檔是[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-基礎副檔名為.resx 檔。 資源檔包含在解決方案中使用的字串翻譯的版本。 如需詳細資訊，請參閱[應用程式中的資源](http://go.microsoft.com/fwlink/?LinkID=155844)。  
  
> [!NOTE]  
>  將只有字串資源加入至 SharePoint 方案的資源檔。 資源編輯器可讓您將非字串資源，雖然非字串資源不會部署至 SharePoint。  
  
## <a name="resource-files"></a>資源檔  
 有三種類型的資源檔： default、 語言中性和特定的語言。  
  
|資源檔類型|描述|  
|------------------------|-----------------|  
|預設|也稱為後援資源，預設資源檔包含預設文化特性，例如英文當地語系化的字串。 如果找不到指定的語言沒有當地語系化的資源檔，會使用它們。 預設資源不會有不同的檔案，它們儲存在主應用程式組件。|  
|語言中性|資源檔，其中包含當地語系化的語言，但不是特定文化特性的字串。 例如，"fr"的法文。|  
|特定語言|資源檔，其中包含當地語系化的語言和文化特性的字串。 例如，"FR-CA 」 為加拿大法文。|  
  
 如需詳細資訊，請參閱[階層式組織當地語系化的資源](http://go.microsoft.com/fwlink/?LinkId=178360)。  
  
 若要在您開發中的 SharePoint 專案中指定預設資源檔[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，選擇**因語言而異 （Invariant 國家/地區）**文化特性清單中的**加入資源**對話方塊時您將資源檔。  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>當地語系化 Visual Studio SharePoint 方案  
 當您將當地語系化的方案時，您應該考慮您的方案會顯示給使用者的文字資訊的所有。 告知性訊息、 錯誤訊息和[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]字串必須進行轉譯，而且這些翻譯放在資源檔。  
  
 資源檔中的每個字串都有唯一的識別碼。 使用相同的識別項中每個資源檔的已翻譯字串。 比方說，如果"String1"是在預設資源檔中的第一個字串的識別項，使用相同的識別項中的特定語言資源檔案的第一個字串。  
  
 有三個區域，您通常會當地語系化中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 應用程式： 功能、 ASPX 網頁標記中，與程式碼。 為了說明起見，下列各節會假設您有想要當地語系化成德文和日文 SharePoint 方案。 預設語言為英文。  
  
### <a name="localizing-features"></a>當地語系化功能  
 若要當地語系化的功能，您必須取代的已翻譯的標題和字串在當地語系化的資源檔參考的運算式中的硬式編碼的標題和描述的功能。 進行這項變更中的**功能設計工具**中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱[如何： 當地語系化功能](../sharepoint/how-to-localize-a-feature.md)。  
  
 若要為德文和日文當地語系化您英文版的功能，您必須將三個資源檔的專案項目加入至專案： 一個英文、 德文，其中，一個用於日文。 功能資源檔不能用來當地語系化 ASPX 標記或程式碼;它們需要不同的資源檔案。  
  
 您建立的功能資源檔之後，將翻譯的字串加入它們。 存取當地語系化的字串格式如下的運算式：  
  
```  
$Resources:String ID  
```  
  
 功能中的資源[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]一律名為資源。 如果您選取的語言而異，文化特性以外的語言[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]加入至資源檔名稱。 例如，如果您新增的語言而異 （預設值） 的功能資源檔，它稱為 Resources.resx。 如果您選取的日文 （日本） 文化特性來加入特定語言功能資源，檔案也稱為 Resources.ja JP.resx。 功能資源檔名稱會自動指派，而且無法變更。  
  
 功能資源的範圍是本機會加入至功能。 若要建立可由方案中的任何功能或項目檔案的資源，新增**全域資源檔案**專案項目，而不是功能資源檔。 **全域資源檔案**專案項目位於**2010年**下的資料夾**SharePoint**中**加入新項目** 對話方塊。 全域資源檔案部署到 SharePoint 根資料夾的 \Resources 資料夾。  
  
### <a name="localizing-aspx-page-markup"></a>當地語系化 ASPX 網頁標記  
 若要當地語系化[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面，專案中加入三個資源檔的專案項目： 一個英文、 德文，其中，一個用於日文。 如果您不需要當地語系化除了標記之外的程式碼，您可以改為加入全域資源檔案。  
  
 提供的預設語言資源檔案的名稱。 提供相同的名稱加上的特定語言的文化特性的當地語系化的資源檔[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，德文的 MyAppResources.de DE.resx 和 MyAppResources.ja-JP.resx 日文。  
  
 設定**部署類型**屬性的每個資源檔**AppGlobalResource**。 這會導致要部署到 App_GlobalResources 資料夾，它們是適用於所有的 ASPX 頁面並在方案中的控制項的資源檔。 App_GlobalResources 資料夾位於 C:\inetpub\wwwroot\wss\VirtualDirectories\\< 連接埠號碼\>\App_GlobalResources。  
  
> [!NOTE]  
>  如果您使用非全域資源檔案，請將它們移至專案項目資料夾中，若要啟用的部署類型的屬性和其他 SharePoint 特有的屬性。  
  
 ASPX 標記資源檔案也可用來當地語系化程式碼。 如果您使用資源當地語系化 ASPX 標記除了程式碼，將 [建置動作] 屬性設定的每個檔案做為內嵌資源，讓資源来編譯至附屬組件。 不過，如果您使用的資源檔案只是為了當地語系化標記，您可以防止檔案被編譯成主應用程式組件的內容 （選擇性） 變更 建置動作。  
  
 ASPX 網頁及控制項標記中的所有硬式編碼屬性字串取代運算式格式如下：  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如：  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 ASPX 為文字，使用運算式格式如下：  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如:   
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 如需詳細資訊，請參閱[如何： 當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)。  
  
### <a name="localizing-code"></a>當地語系化程式碼  
 除了當地語系化功能字串和[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]標記中，您也必須將訊息字串和出現在您方案的程式碼中的錯誤字串當地語系化。 當地語系化資訊和附屬組件中所包含的錯誤訊息。 附屬組件包含的使用者都看得到，例如字串[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]文字和輸出訊息類似的例外狀況。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用標準.NET Framework 的中樞和支點模型。 集線器或程式主要組件，包含預設語言資源。 支點或附屬組件，包含語言特定資源。 如需詳細資訊，請參閱[封裝和部署資源](http://go.microsoft.com/fwlink/?LinkId=179280)。 從資源 (.resx) 檔編譯附屬組件。 當您將語言特定資源檔加入您的專案和方案套件，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將資源檔編譯至附屬組件名為*專案名稱*。.resources.dll。  
  
 如同 ASPX 標記當地語系化 SharePoint 應用程式程式碼，將個別的資源檔專案項目加入至您的專案。一個用於預設語言，另一個用於每個當地語系化語言。 不過，如前所述，如果您已經有資源檔來當地語系化 ASPX 標記，您可以重複使用它們的當地語系化程式碼。 如果您需要建立資源檔，提供的預設語言資源檔案副檔名為.resx 附加您選擇的名稱。 名稱相同的名稱加上的特定語言的文化特性的當地語系化的資源檔[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 每個資源檔的 [建置動作] 屬性設為要在附屬資源組件建立內嵌資源。  
  
 若要建立的附屬組件，建置專案，然後再將檔案做為其他組件透過**進階** 索引標籤**封裝設計工具**。 當加入組件，前面加上文化特性[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]資料夾的位置路徑，例如 DE-DE\\*專案項目名稱*。.resources.dll。 這可讓封裝包含具有相同名稱的檔案。  
  
 在您的程式碼取代硬式編碼字串呼叫<xref:System.Web.HttpContext.GetGlobalResourceObject%2A>方法使用下列語法：  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 如需詳細資訊，請參閱[如何： 當地語系化程式碼](../sharepoint/how-to-localize-code.md)。  
  
#### <a name="web-part-code-localization"></a>Web 組件程式碼當地語系化  
 Web 組件包含自訂屬性編輯器 功能，包括使用硬式編碼的字串，例如 WebDisplayName、 類別和 WebDescription 的程式碼屬性。 若要取代這些屬性的字串值，建立個別的類別衍生自屬性類別。 在這些類別中，設定該屬性的屬性。 屬性內容取決於基底類別。 例如，WebDisplayName 屬性是 DisplayNameValue 而 WebDescription 屬性內容是 DescriptionValue。  
  
 在衍生類別中，參考的字串識別碼從資源檔和 ResourceManager 来取得之物件的當地語系化的值的字串 id。 此值傳回到屬性編輯器。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 當地語系化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何： 當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何： 當地語系化程式碼](../sharepoint/how-to-localize-code.md)   
 [如何： 將資源檔](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  