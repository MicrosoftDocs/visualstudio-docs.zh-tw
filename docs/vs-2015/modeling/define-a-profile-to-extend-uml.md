---
title: 定義要擴充 UML 的設定檔 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2886e454e9986e63cbc3496d3ef5b0664e85dede
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851591"
---
# <a name="define-a-profile-to-extend-uml"></a>定義要擴充 UML 的設定檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以定義*UML 設定檔*針對特定用途自訂標準模型項目。 設定檔會定義一或多個*UML 造型*。 造型可用來標記代表特殊種類物件的類型。 造型也可擴充項目的屬性清單。  
  
 數個設定檔會與支援的 Visual Studio 版本一起安裝。 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。 如需有關這些設定檔，以及有關如何套用造型的詳細資訊，請參閱[來自訂您的模型，使用設定檔和造型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)。  
  
 您可以定義專屬設定檔來調整 UML 並將其擴充至專屬商業領域或架構。 例如：  
  
- 如果您經常定義網站，則可以定義專屬設定檔，以提供可套用至類別圖中類別的 «網頁» 造型。 您接著可以使用類別圖來規劃網站。 每個 «網頁» 類別都會有頁面內容、樣式等的額外屬性。  
  
- 如果您開發銀行業務軟體，則可以定義提供 «帳戶» 造型的設定檔。 您接著可以使用類別圖來定義不同類型的帳戶，以及顯示其間的關聯性。  
  
  您可以將專屬設定檔散發給您的小組。 每個小組成員都可以安裝您的設定檔。 這可讓他們編輯和建立使用其造型的模型。  
  
> [!NOTE]
>  如果您在所編輯的模型中套用設定檔的造型，然後與其他人員共用模型，則他們應該在自己的電腦上安裝相同的設定檔。 否則，他們將無法看到您已經使用的造型。  
  
 設定檔通常是較大一部分[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]延伸模組。 例如，您可以定義將模型的某些組件轉譯為程式碼的命令。 您可以定義設定檔，而使用者必須將它套用至他們想要轉譯的套件。 您會在單一 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充功能中一併散發新命令和設定檔。  
  
 您也可以定義設定檔的當地語系化變化。 載入您擴充功能的使用者會看到適合其專屬文化特性的變化。  
  
##  <a name="DefineProfile"></a> 如何定義設定檔  
  
#### <a name="to-define-a-uml-profile"></a>定義 UML 設定檔  
  
1.  建立副檔名為 `.profile` 的新 XML 檔案。  
  
2.  加入造型定義根據所述的指導方針[設定檔的結構](#Schema)。  
  
3.  將設定檔加入 Visual Studio 擴充功能 (`.vsix` 檔案)。 您可以建立設定檔的新擴充功能，或將設定檔加入現有擴充功能。  
  
     請參閱下一步 區段中，[如何將設定檔新增至 Visual Studio 擴充功能](#AddProfile)。  
  
4.  在電腦上安裝擴充功能。  
  
    1.  按兩下副檔名為 `.vsix` 的擴充檔。  
  
    2.  重新啟動 Visual Studio。  
  
5.  確認已安裝設定檔。  
  
    1.  在 [UML 總管] 中，選取模型。  
  
    2.  在 [屬性] 視窗中，按一下**設定檔**屬性。 設定檔將出現在功能表中。 設定設定檔旁邊的核取記號。  
  
    3.  選取您的設定檔定義其造型的項目。 在 [屬性] 視窗中，按一下**造型**屬性。 您的造型會出現在清單中。 針對其中一個造型，設定核取記號。  
  
    4.  如果您的設定檔定義這個造型的其他屬性，請展開造型屬性來查看它們。  
  
6.  將擴充檔傳送給 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的其他使用者，以安裝在其電腦上。  
  
##  <a name="AddProfile"></a> 如何將設定檔新增至 Visual Studio 擴充功能  
 若要安裝設定檔，以及讓您將它傳送給其他使用者，則必須將設定檔加入 Visual Studio 擴充功能。 如需詳細資訊，請參閱 <<c0> [ 部署 Visual Studio 擴充功能](http://go.microsoft.com/fwlink/?LinkId=160780)。  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>在新的 Visual Studio 擴充功能中定義設定檔  
  
1. 建立 Visual Studio 擴充功能專案。  
  
   > [!NOTE]
   >  您必須已安裝 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 才能使用此程序。  
  
   1.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
   2.  在**新的專案**對話方塊的 **已安裝的範本**，展開**Visual C#**，按一下 **擴充性**，然後按一下**VSIX 專案**。 設定專案名稱，然後按一下**確定**。  
  
2. 將設定檔加入專案。  
  
   -   在 [方案總管] 中，以滑鼠右鍵按一下專案，指向**新增**，然後按一下**現有項目**。 在對話方塊中，找到您的設定檔名稱。  
  
3. 設定設定檔**複製到輸出**屬性。  
  
   1.  在 方案總管 中，以滑鼠右鍵按一下 設定檔，然後**屬性**。  
  
   2.  在 [屬性] 視窗中，設定**複製到輸出目錄**屬性設**永遠複製**。  
  
4. 在 [方案總管] 中，開啟 `source.extension.vsixmanifest`。  
  
    此檔案會在擴充功能資訊清單編輯器中開啟。  
  
5. 在 **資產**頁面上，加入描述設定檔的資料列：  
  
   -   按一下 [新增] 。 設定欄位**加入新資產**，如下所示的對話方塊。  
  
   -   設定**型別**至 `Microsoft.VisualStudio.UmlProfile`  
  
        這不是其中一個下拉式清單選項。 請使用鍵盤輸入這個名稱。  
  
   -   按一下 **檔案系統上的**，然後選取您的設定檔的名稱，例如 `MyProfile.profile`  
  
6. 建置專案。  
  
7. **若要偵錯設定檔**，按下 f5 鍵。  
  
    Visual Studio 的實驗執行個體隨即開啟。 在這種情況下，請開啟模型專案。 在 [UML 總管] 中，選取模型的根項目，並且在 [屬性] 視窗中選取您的設定檔。 然後選取模型內的項目，並選取您為這些項目定義的造型。  
  
8. **若要擷取 VSIX 進行部署**  
  
   1.  在 Windows 檔案總管中，開啟資料夾 **.\bin\Debug**或是 **.\bin\Release**若要尋找 **.vsix**檔案。 這是 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充檔。 該檔案可以安裝在您的電腦上，以及傳送給其他 Visual Studio 使用者。  
  
   2.  安裝擴充功能：  
  
       1.  按兩下 `.vsix` 檔案。 [Visual Studio 擴充功能安裝程式] 隨即啟動。  
  
       2.  重新啟動任何正在執行的 Visual Studio 執行個體。  
  
   如果尚未安裝 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]，則可以將下列替代程序用於小型擴充功能。  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>在未使用 Visual Studio SDK 的情況下定義設定檔擴充功能  
  
1.  建立包含下列三個檔案的 Windows 目錄：  
  
    -   *一個* `.profile`  
  
    -   `extension.vsixmanifest`  
  
    -   `[Content_Types].xml` - 使用方括號，輸入此處所示的這個名稱  
  
2.  編輯 `[Content_Types].xml` 以包含下列文字。 請注意，它包含每個副檔名的項目。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3.  複製現有 `extension.vsixmanifest`，並使用 XML 編輯器進行編輯。 變更 [識別碼]、[名稱] 和 [內容] 節點。  
  
    -   您可以在這個目錄中尋找 `extension.vsixmanifest` 範例：  
  
         *磁碟機* **: \Program Files\Microsoft Visual Studio [版本] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**  
  
    -   [內容] 節點應該如下：  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4.  將三個檔案壓縮成一個 ZIP 壓縮檔。  
  
     在 Windows 檔案總管中，選取三個檔案，請以滑鼠右鍵按一下，指向**傳送到**，然後按一下**壓縮 (zipped) 資料夾**。  
  
5.  重新命名 ZIP 壓縮檔，並將其副檔名從 `.zip` 變更為 `.vsix`。  
  
6.  若要在任何具有適當 Visual Studio 版本的電腦上安裝設定檔，請按兩下 `.vsix` 檔案。  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>從 Visual Studio 擴充功能安裝 UML 設定檔  
  
1.  在 Windows 檔案總管中按兩下 `.vsix` 檔案，或在 Visual Studio 內開啟它。  
  
2.  按一下 **安裝**中出現的對話方塊。  
  
3.  若要解除安裝或暫時停用擴充功能，開啟**擴充功能和更新**從**工具**功能表。  
  
##  <a name="Localized"></a> 如何定義當地語系化設定檔  
 您可以針對不同的文化特性或語言定義不同的設定檔，並將它們全部封裝到相同的擴充功能。 使用者在載入您的擴充功能時，會看到您針對他們的文化特性所定義的設定檔。  
  
 您一律必須提供預設的設定檔。 如果您尚未定義使用者文化特性的設定檔，則使用者會看到預設設定檔。  
  
#### <a name="to-define-a-localized-profile"></a>定義當地語系化設定檔  
  
1.  建立設定檔，如先前各節中所述[如何定義設定檔](#DefineProfile)並[如何將設定檔新增至 Visual Studio 擴充功能](#AddProfile)。 這是預設設定檔，將用於任何未提供當地語系化設定檔的安裝。  
  
2.  在與預設設定檔相同的目錄中，加入新的目錄。  
  
    > [!NOTE]
    >  如果您是使用 Visual Studio 擴充功能專案來建置擴充功能，請使用 [方案總管] 將新的資料夾加入專案。  
  
3.  將新目錄的名稱變更為當地語系化文化特性的 ISO 簡短程式碼 (例如 `bg` 代表保加利亞文或 `fr` 代表法文)。 您應該使用中性文化特性代碼，通常為兩個字母，而不是特定文化特性 (例如 `fr-CA`)。 如需文化特性代碼的詳細資訊，請參閱[CultureInfo.GetCultures 方法](http://go.microsoft.com/fwlink/?LinkId=160782)，以提供完整的文化特性代碼清單。  
  
4.  將預設設定檔的複本加入新的目錄。 請不要變更其檔案名稱。  
  
     樣本[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]擴充功能資料夾，再建置或壓縮成`.vsix`檔案中，會包含下列資料夾和檔案：  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    >  您不應該將設定檔之本地語系化版本的參考插入 `extension.vsixmanifest`。 所複製設定檔的名稱必須與父資料夾中設定檔的名稱相同。  
  
5.  編輯設定檔的新複本，方法是將使用者看到的所有組件都翻譯為目標語言 (例如 `displayName` 屬性)。  
  
6.  您可以針對所需數目的文化特性，建立其他文化特性資料夾和當地語系化設定檔。  
  
7.  建置 Visual Studio 擴充功能，方法是建置擴充功能專案或壓縮所有檔案 (如前面小節所述)。  
  
##  <a name="Schema"></a> 設定檔結構  
 UML 設定檔的 XSD 檔案可在下列範例：[設定造型和設定檔 XSD](http://go.microsoft.com/fwlink/?LinkID=213811)。 為了協助您編輯設定檔，請將 `.xsd` 檔案安裝在下列位置：  
  
 **%ProgramFiles%\Microsoft visual Studio [版本] \Xml\Schemas**  
  
 本節使用 C# 設定檔做為範例。 您可以在下列位置看到完整設定檔定義：  
  
 *磁碟機* **: \Program Files\Microsoft Visual Studio [版本] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**  
  
 在您的安裝中，這個路徑的第一個部分可能不同。  
  
 如需.NET 設定檔的詳細資訊，請參閱[UML 模型的標準造型](../modeling/standard-stereotypes-for-uml-models.md)。  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>UML 設定檔定義的主要區段  
 每個設定檔都包含下列內容：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<profile dslVersion="1.0.0.0"   
       name="CSharpProfile" displayName="C# Profile"   
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">  
  <stereotypes>...</stereotypes>  
  <metaclasses>...</metaclasses>  
  <propertyTypes>...</propertyTypes>  
</profile>  
```  
  
> [!NOTE]
>  稱為 `name` 的屬性不得包含空格或標點符號。 出現在使用者介面中的屬性 `displayName` 應該是有效的 XML 字串。  
  
 每個設定檔都包含三個主要區段。 它們以反向順序顯示如下：  
  
-   `<propertyTypes>` - 用於 stereotypes 區段中所定義屬性的類型清單。  
  
-   `<metaclasses>` - 套用此設定檔中造型的模型項目類型清單 (例如 IClass、IInterface、IOperation、IDependency)。  
  
-   `<stereotypes>` - 造型定義。 每個定義都包括加入目標模型項目之屬性的名稱和類型。  
  
#### <a name="property-types"></a>屬性類型  
 `<propertyTypes>`區段可宣告的使用中的屬性型別清單`<stereotypes>`一節。 有兩種屬性類型：外部和列舉。  
  
 外部類型宣告標準 .NET 類型的完整名稱：  
  
```  
<externalType name="System.String" />  
```  
  
 列舉類型定義一組常值：  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Metaclasses  
 `<metaclasses>` 區段是可定義此設定檔中造型的模型項目類型清單：  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 您可以做為 metaclasse 的模型項目和關聯性類型的完整清單，請參閱[模型項目類型](#Elements)。  
  
#### <a name="stereotype-definition"></a>造型定義  
 `<stereotypes>` 區段包含一或多個造型定義：  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 每個造型都會列出可套用它的一或多個模型項目或關聯性類型。 您可以提供基底類型的名稱，以包括其所有衍生類型。 例如，如果您指定 `Microsoft.VisualStudio.Uml.Classes.IType`，則可以將造型套用至 `IClass`、`IInterface``IEnumeration` 和數個其他類型的項目。  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 `name` 的 `metaclassMoniker` 屬性是與 `<metaClasses>` 區段中項目的連結。  
  
> [!NOTE]
>  Moniker 名稱的開頭必須是 `/yourProfileName/`，其中 `yourProfileName` 定義於設定檔的 `name` 屬性中 (在此範例中為 "CSharpProfile")。 Moniker 的結尾是 metaclasses 區段中其中一個項目的名稱。  
  
 每個造型都可以列出零或多個屬性，並且會將這些屬性加入套用它的任何模型項目。 `<propertyType>`包含其中一個類型中所定義的連結`<propertyTypes>`一節。 連結必須是參照 `<externalTypeMoniker>` 的 `<externalType>,` 或參照 `<enumerationTypeMoniker>` 的 `<enumerationType>`。 同樣地，連結的開頭是您設定檔的名稱。  
  
```  
  <properties>  
    <property name="IsStatic"   
            displayName="Is Static" defaultValue="false">  
      <propertyType>  
<externalTypeMoniker   
               name="/CSharpProfile/System.Boolean" />  
      </propertyType>  
    </property>  
    <property name="PackageVisibility"   
              displayName="Package Visibility"  
              defaultValue="internal">  
      <propertyType>  
        <enumerationTypeMoniker   
              name="/CSharpProfile/PackageVisibility"/>  
      </propertyType>  
    </property>  
  </properties>  
</stereotype>  
```  
  
##  <a name="Elements"></a> 模型項目類型  
 您可以定義造型的類型會列在[UML 模型項目類型](../modeling/uml-model-element-types.md)。  
  
## <a name="troubleshooting"></a>疑難排解  
 我的造型未出現我的 UML 模型。  
 您必須在套件或模型中選取設定檔。 造型接著會出現在套件或模型內的項目上。 如需詳細資訊，請參閱 <<c0> [ 新增造型，加入 UML 模型項目](../modeling/add-stereotypes-to-uml-model-elements.md)。  
  
 當我開啟 UML 模型時，就會出現下列錯誤： **VS1707： 無法載入下列設定檔，因為發生序列化錯誤： MyProfile.profile**  
 1.  確認 .profile 的基本 XML 語法正確。  
  
2. 確定每個 Moniker 名稱的格式都是 /profileName/nodeName。 profileName 是根設定檔節點中 name 屬性的值。 nodeName 是 metaclass、externalType 或 enumerationType 的 name 屬性值。  
  
3. 確定語法如下所示，且如所示_磁碟機_**: \Program Files\Microsoft Visual Studio [版本] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .  
  
4. 解除安裝錯誤擴充功能。 在 [工具]  功能表上，按一下 [擴充功能和更新] 。  
  
   -   如果擴充功能未出現，請參閱下一個項目。  
  
5. 重建 VSIX 檔案，並在 Windows 檔案總管中開啟它進行重新安裝。 重新啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
   延伸模組不會出現在 [延伸模組管理員] 中，但當您嘗試重新安裝它時，會顯示下列訊息：**延伸模組已安裝所有適用的產品。**  
   1.  移除的子資料夾中的擴充檔案*LocalAppData*\Microsoft\VisualStudio\\[version] \Extensions\  
  
   -   若要查看*LocalAppData*，您必須在 Windows 檔案總管資料夾選項 的 檢視 索引標籤中設定顯示隱藏的檔案和資料夾。  
  
   -   *LocalAppData*通常是在 C:\Users\\*userName*\AppData\Local\  
  
6. 重新啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [將造型加入 UML 模型項目](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [自訂您的模型，使用設定檔和造型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [UML 模型的標準造型](../modeling/standard-stereotypes-for-uml-models.md)   
 [範例： 依據造型色彩 UML 項目](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [範例： 設定造型、 設定檔 XSD](http://go.microsoft.com/fwlink/?LinkID=213811)



