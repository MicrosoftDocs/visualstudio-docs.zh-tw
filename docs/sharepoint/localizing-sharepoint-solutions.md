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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bcd11d7860e1d191479d4a2ea5f9fac78dcdfe2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189216"
---
# <a name="localize-sharepoint-solutions"></a>當地語系化 SharePoint 方案

  準備您的應用程式以供全球使用的流程，也稱為「當地語系化」。 當地語系化是將資源轉譯成特定的文化特性。 如需詳細資訊，請參閱[全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)。 本主題提供如何將 SharePoint 方案當地語系化的總覽。

 若要將方案當地語系化，您可以從程式碼中移除硬式編碼的字串，並將其抽象化為資源檔。 資源檔是以 *.resx*副檔名 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]為基礎的檔案。 資源檔包含解決方案中所使用之字串的轉譯版本。 如需詳細資訊，請參閱[應用程式中的資源](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100))。

> [!NOTE]
> 只將字串資源加入至 SharePoint 方案資源檔。 雖然資源編輯器可讓您新增非字串的資源，但非字串的資源不會部署至 SharePoint。

## <a name="resource-files"></a>資源檔
 資源檔有三種類型：預設、非語言相關，以及特定語言。

|資源檔案類型|描述|
|------------------------|-----------------|
|Default|也稱為「回復資源」，預設資源檔包含為預設文化特性（例如英文）當地語系化的字串。 如果找不到指定語言的當地語系化資源檔，則會使用它們。 預設資源沒有個別的檔案，而是儲存在主要應用程式元件中。|
|語言中性|資源檔，其中包含針對語言當地語系化的字串，但不含特定的文化特性。 例如，"fr" 代表法文。|
|語言特定|包含針對語言和文化特性當地語系化之字串的資源檔。 例如，"fr-CA" 代表加拿大法文。|

 如需詳細資訊，請參閱[階層式組織當地語系化的資源](../ide/globalizing-and-localizing-applications.md)。

 若要在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中開發的 SharePoint 專案中指定預設資源檔，請在新增資源檔時，于 [**加入資源**] 對話方塊的 [文化特性] 清單中選擇 [不**變語言（非變異國家）** ]。

## <a name="localize-visual-studio-sharepoint-solutions"></a>當地語系化 Visual Studio SharePoint 方案
 當您將解決方案當地語系化時，您應該考慮解決方案向使用者顯示的所有文字資訊。 您必須轉譯參考用訊息、錯誤訊息和 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 字串，以及放在資源檔中的翻譯。

 資源檔中的每個字串都有唯一的識別碼。 針對每個資源檔中的翻譯字串使用相同的識別碼。 例如，如果 "String1" 是預設資源檔中第一個字串的識別碼，請針對語言特定資源檔中的第一個字串使用相同的識別碼。

 您通常會在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 應用程式中當地語系化三個區域：功能、ASPX 頁面標記和程式碼。 為方便說明，下列各節假設您有想要當地語系化為德文和日文的 SharePoint 方案。 預設語言為英文。

### <a name="localize-features"></a>當地語系化功能
 若要將功能當地語系化，您必須將功能的硬式編碼標題和描述取代為參考當地語系化資源檔中已翻譯標題和字串的運算式。 您會在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的**功能設計**工具中進行這項變更。 如需詳細資訊，請參閱[如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)。

 若要將您的英文功能當地語系化為德文和日文，請將三個資源檔專案專案新增至您的專案：一個用於英文，一個用於德文，另一個用於日文。 功能資源檔不能用來當地語系化 ASPX 標記或程式碼;需要個別的資源檔。

 建立功能資源檔之後，請將翻譯的字串加入其中。 使用下列格式的運算式來存取當地語系化的字串：

```aspx-csharp
$Resources:String ID
```

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的功能資源一律會命名為 Resources。 如果您選取非變異語言以外的語言，則會將文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 新增至資源檔名稱。 例如，如果您加入不變的語言（預設）功能資源檔，則會稱為*Resources .resx*。 如果您藉由選取 [日文（日本）] 文化特性來加入特定語言的功能資源，該檔案就會被稱為*Resources. ja-jp .resx*。 功能資源檔名稱會自動指派，且無法變更。

 功能資源的範圍是其新增的功能的區域。 若要建立方案中任何功能或元素檔案可以使用的資源，請加入**全域資源檔**專案專案，而不是功能資源檔。 [**全域資源檔**] 專案專案位於 [**加入新專案**] 對話方塊的 [ **SharePoint** ] 底下的 [ **2010** ] 資料夾中。 全域資源檔會部署到 SharePoint 根資料夾的 \Resources 資料夾。

### <a name="localize-aspx-page-markup"></a>當地語系化 ASPX 頁面標記
 若要將 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 頁面當地語系化，您可以將三個資源檔專案新增至您的專案：一個用於英文，一個用於德文，另一個用於日文。 如果除了標記之外，您不需要當地語系化程式碼，您可以改為加入全域資源檔。

 提供預設語言資源檔的名稱。 指定當地語系化的資源檔，並以語言特定的文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]附加相同的名稱。 例如，MyAppResources.de 的德文和*MyAppResources*的 *.resx* ，適用于日文。

 將每個資源檔的 **部署類型** 屬性設定為**appglobalresource**。 這會使資源檔部署至 App_GlobalResources 資料夾，供方案中的所有 ASPX 頁面和控制項使用。 App_GlobalResources 資料夾位於 C:\inetpub\wwwroot\wss\VirtualDirectories\\< 埠號碼\>\App_GlobalResources。

> [!NOTE]
> 如果您使用非全域資源檔，請將它們移至專案專案資料夾中，以啟用 [部署類型] 屬性和其他 SharePoint 特定屬性。

 ASPX 標記資源檔也可以用來將程式碼當地語系化。 如果您要使用資源來當地語系化 ASPX 標記以外的程式碼，請將每個檔案的 [組建動作] 屬性設定保留為 [內嵌資源]，讓資源編譯成附屬元件。 不過，如果您只使用資源檔來將標記當地語系化，則可以選擇性地將 [組建動作] 變更為 [內容]，以防止將檔案編譯成主要應用程式元件。

 將 ASPX 頁面中所有硬式編碼的屬性字串取代為下列格式的運算式，並將其控制項標記為：

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 例如:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 若為 ASPX 做為文字，請使用下列格式的運算式：

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 例如:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 如需詳細資訊，請參閱[如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)。

### <a name="localize-code"></a>當地語系化程式碼
 除了當地語系化功能字串和 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 標記之外，您還必須將出現在方案程式碼中的訊息字串和錯誤字串當地語系化。 當地語系化的資訊和錯誤訊息會包含在附屬元件中。 附屬元件包含可對使用者顯示的字串，例如 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 文字，以及例外狀況之類的輸出訊息。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用標準的 .NET Framework 中樞和輪輻模型。 中樞或主要程式元件包含預設的語言資源。 輪輻或附屬元件包含語言特定的資源。 如需詳細資訊，請參閱[封裝和部署資源](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100))。 附屬元件是從資源檔（ *.resx*）進行編譯。 當您將特定語言的資源檔新增至您的專案和方案套件時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將資源檔編譯成名為 *{Project Name} .resources .dll*的附屬元件。

 如同 ASPX 標記，請將個別的資源檔專案專案新增至您的專案，以當地語系化 SharePoint 應用程式程式碼;一個用於預設語言，另一個用於每個當地語系化的語言。 不過，如先前所述，如果您已經有用來當地語系化 ASPX 標記的資源檔，您可以重複使用它們來當地語系化程式碼。 如果您需要建立資源檔，請為預設的語言資源檔指定您選擇的名稱，並附上 *.resx*副檔名。 將當地語系化的資源檔命名為與語言特定文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]一起附加的相同名稱。 將每個資源檔的 [組建動作] 屬性設定為 [內嵌資源]，以啟用附屬資源元件的建立。

 若要建立附屬元件，請建立專案，然後透過**封裝設計**工具的 [ **Advanced** ] 索引標籤，將檔案新增為其他元件。 加入元件時，請在位置路徑前面加上文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 資料夾，例如*取消刪除\\{專案專案名稱} .resources .dll*。 這可讓封裝包含具有相同名稱的檔案。

 在您的程式碼中，使用下列語法，將硬式編碼的字串取代為 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法的呼叫：

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 如需詳細資訊，請參閱[如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)。

#### <a name="web-part-code-localization"></a>Web 元件程式碼當地語系化
 Web 元件包括自訂的屬性編輯器功能，其中包含使用硬式編碼字串的程式碼屬性，例如 WebDisplayName、Category 和 WebDescription。 若要取代這些屬性的字串值，請建立衍生自屬性類別的個別類別。 在這些類別中，設定屬性的屬性。 屬性屬性取決於基類。 例如，WebDisplayName 屬性屬性是 DisplayNameValue，而 WebDescription 屬性屬性則是 DescriptionValue。

 在衍生類別中，從資源檔和 ResourceManager 物件中參考字串識別碼，以取得字串識別碼的當地語系化值。 將此值傳回給屬性編輯器屬性。

## <a name="see-also"></a>請參閱
- [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)
- [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)
- [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)
- [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)
- [如何：使用資源檔來指定當地語系化名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
