---
title: 當地語系化 SharePoint 方案 |Microsoft Docs
description: 將程式碼中的硬式編碼字串從程式碼中移除，並將它們抽象化為 XML 型資源 ( .resx) 包含翻譯字串的檔案，以當地語系化 SharePoint 方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16cb372e5acf719d3edc79f081cff6f4b0396b6a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304266"
---
# <a name="localize-sharepoint-solutions"></a>當地語系化 SharePoint 方案

  準備您的應用程式，使其可在全球使用的程式稱為「當地語系化」（當地語系化）。 當地語系化會將資源轉譯成特定文化特性。 如需詳細資訊，請參閱 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)。 本主題提供如何將 SharePoint 方案當地語系化的總覽。

 若要當地語系化方案，請從程式碼中移除硬式編碼的字串，並將它們抽象化為資源檔。 資源檔是副檔名為 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] *.resx* 的檔案。 資源檔包含解決方案中所使用之字串的翻譯版本。 如需詳細資訊，請參閱 [應用程式中的資源](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100))。

> [!NOTE]
> 只將字串資源加入至 SharePoint 方案資源檔。 雖然資源編輯器可讓您新增非字串資源，但是非字串資源也不會部署到 SharePoint。

## <a name="resource-files"></a>資源檔
 資源檔有三種類型：預設、非語言相關，以及特定語言。

|資源檔案類型|描述|
|------------------------|-----------------|
|預設|預設資源檔也稱為 fallback 資源，包含針對預設文化特性（例如英文）當地語系化的字串。 如果找不到指定語言的當地語系化資源檔，則會使用它們。 預設資源沒有個別的檔案，它們會儲存在主要應用程式元件中。|
|非語言相關|資源檔，其中包含針對語言（但不是特定文化特性）當地語系化的字串。 例如，"fr" 代表法文。|
|特定語言|資源檔，其中包含針對語言和文化特性當地語系化的字串。 例如，"fr-CA" 適用于加拿大法文。|

 如需詳細資訊，請參閱 [階層式組織的當地語系化資源](../ide/globalizing-and-localizing-applications.md)。

 若要在中，指定您在中開發的 SharePoint 專案預設資源檔 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請在新增資源檔時，在 [**加入資源**] 對話方塊的 [文化特性] 清單中選擇 [不區分文化特性] (非變異 **國家)** 。

## <a name="localize-visual-studio-sharepoint-solutions"></a>當地語系化 Visual Studio SharePoint 方案
 當您將方案當地語系化時，您應該考慮您的解決方案向使用者顯示的所有文字資訊。 您必須將參考訊息、錯誤訊息和 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 字串轉譯，以及將這些翻譯放在資源檔中。

 資源檔中的每個字串都有唯一的識別碼。 針對每個資源檔中的翻譯字串使用相同的識別碼。 例如，如果 "String1" 是預設資源檔中第一個字串的識別碼，請針對特定語言資源檔中的第一個字串使用相同的識別碼。

 您通常會在 SharePoint 應用程式中將下列三個區域當地語系化 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ：功能、ASPX 頁面標記和程式碼。 為了方便說明，下列各節假設您有想要當地語系化成德文和日文的 SharePoint 方案。 預設語言為英文。

### <a name="localize-features"></a>當地語系化功能
 若要將功能當地語系化，您必須將功能的硬式編碼標題和描述取代為參考當地語系化資源檔中翻譯標題和字串的運算式。 您可以在的 **功能設計** 工具中進行這項變更 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)。

 若要將您的英文功能當地語系化為德文和日文，請將三個資源檔專案專案新增至您的專案：一個用於英文、一個用於德文，另一個用於日文。 功能資源檔不能用來當地語系化 ASPX 標記或程式碼;需要個別的資源檔。

 在您建立功能資源檔之後，請在其中新增已轉譯的字串。 使用下列格式的運算式來存取當地語系化的字串：

```aspx-csharp
$Resources:String ID
```

 中的功能資源 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 一律稱為資源。 如果您選取非變異語言以外的語言，則會將文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 新增至資源檔名稱。 例如，如果您將非變異語言新增 (預設) 功能資源檔，它就稱為 *Resources*。 如果您藉由選取日文 (日本) 的文化特性來新增特定語言的功能資源，則該檔案稱為 *Resources. ja-jp. .resx*。 功能資源檔名稱會自動指派，且無法變更。

 功能資源的範圍是其新增的功能所在的區域。 若要建立方案中任何功能或元素檔可使用的資源，請新增 **全域資源檔** 專案專案，而不是功能資源檔。 在 [**加入新專案**] 對話方塊中，[**全域資源檔**] 專案專案位於 [ **SharePoint** ] 下的 [ **2010** ] 資料夾中。 全域資源檔會部署到 SharePoint 根資料夾的 \Resources 資料夾。

### <a name="localize-aspx-page-markup"></a>當地語系化 ASPX 頁面標記
 若要將 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 頁面當地語系化，您可以在專案中加入三個資源檔專案專案：一個用於英文、一個用於德文，另一個用於日文。 如果您不需要當地語系化標記以外的程式碼，您可以改為加入全域資源檔。

 提供預設語言資源檔的名稱。 提供當地語系化的資源檔，並以特定語言的文化特性附加相同的名稱 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 。 例如，適用于德文的 *MyAppResources.de-de .resx* 以及日文的 *MyAppResources. ja-jp .resx* 。

 將每個資源檔的 [ **部署類型** ] 屬性設定為 [ **[appglobalresource**]。 這會導致資源檔部署到 App_GlobalResources 資料夾，供方案中的所有 ASPX 頁面和控制項使用。 App_GlobalResources 資料夾位於 C:\inetpub\wwwroot\wss\VirtualDirectories \\<埠編號 \> \ App_GlobalResources。

> [!NOTE]
> 如果您使用非全域資源檔，請將它們移到專案專案資料夾，以啟用 [部署類型] 屬性和其他 SharePoint 特定屬性。

 ASPX 標記資源檔也可以用來當地語系化程式碼。 如果您使用資源來當地語系化 ASPX 標記以外的程式碼，請將每個檔案的 [組建動作] 屬性設定保留為 [內嵌資源]，使資源編譯成附屬元件。 但是，如果您只使用資源檔來將標記當地語系化，則可以選擇性地將 [組建] 動作變更為 [內容]，以防止將檔案編譯成主要的應用程式元件。

 以下列格式的運算式取代 ASPX 頁面中的所有硬式編碼屬性字串和控制項標記：

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 例如：

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 若為 ASPX 做為文字，請使用下列格式的運算式：

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 例如：

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 如需詳細資訊，請參閱 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)。

### <a name="localize-code"></a>當地語系化程式碼
 除了當地語系化功能字串和標記之外 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ，您還必須將出現在方案程式碼中的訊息字串和錯誤字串當地語系化。 當地語系化的參考和錯誤訊息會包含在附屬元件中。 附屬元件包含使用者可以看到的字串，例如 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 文字和輸出訊息，例如例外狀況。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用標準 .NET Framework 中樞和輪輻模型。 中樞或主要程式元件包含預設語言資源。 輪輻或附屬元件包含特定語言的資源。 如需詳細資訊，請參閱[封裝和部署資源](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100))。 附屬元件會從資源 (*.resx*) 檔案進行編譯。 當您將特定語言的資源檔新增至專案和方案套件時，會將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 資源檔編譯為名為 *{project Name} .resources.dll* 的附屬元件。

 如同 ASPX 標記，將個別資源檔專案專案加入至專案，以當地語系化 SharePoint 應用程式程式碼;一個用於預設語言，另一個用於每個當地語系化的語言。 不過，如先前所述，如果您已經有可當地語系化 ASPX 標記的資源檔，您可以重複使用它們來當地語系化程式碼。 如果您需要建立資源檔，請為預設語言資源檔提供您選擇的名稱，並附加 *.resx* 副檔名。 將當地語系化的資源檔命名為與特定語言文化特性一起附加的相同名稱 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 。 將每個資源檔的 [組建動作] 屬性設定為 [內嵌資源]，以啟用附屬資源元件的建立。

 若要建立附屬元件，請建立專案，然後透過 **封裝設計** 工具的 [ **Advanced** ] 索引標籤，將檔案新增為其他元件。 新增元件時，請在位置路徑前面加上文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 資料夾，例如 *de de \\ {Project Item Name} .resources.dll*。 這可讓封裝包含具有相同名稱的檔案。

 在您的程式碼中，使用下列語法，將硬式編碼的字串取代為對方法的呼叫 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> ：

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 如需詳細資訊，請參閱 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)。

#### <a name="web-part-code-localization"></a>Web 元件程式碼當地語系化
 Web 元件包含自訂屬性編輯器功能，其中包括使用硬式編碼字串的程式碼屬性，例如 WebDisplayName、Category 和 WebDescription。 若要取代這些屬性的字串值，請建立衍生自屬性類別的不同類別。 在這些類別中，設定屬性的屬性。 Attribute 屬性相依于基類。 例如，WebDisplayName 屬性（attribute）屬性（attribute）是 DisplayNameValue，而 WebDescription 屬性（property）屬性（DescriptionValue）。

 在衍生類別中，從資源檔和 ResourceManager 物件參考字串識別碼，以取得字串識別碼的當地語系化值。 將此值傳回至屬性編輯器屬性。

## <a name="see-also"></a>另請參閱
- [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)
- [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)
- [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)
- [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)
- [如何：使用資源檔來指定當地語系化的名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
