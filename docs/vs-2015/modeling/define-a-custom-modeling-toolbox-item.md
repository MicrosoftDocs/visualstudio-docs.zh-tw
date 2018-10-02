---
title: 定義自訂模型工具箱項目 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: bd2d7ff2b31e8975574cb6b2780a352faa1cd663
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488444"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>定義自訂模型工具箱項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[定義自訂模型工具箱項目](https://docs.microsoft.com/visualstudio/modeling/define-a-custom-modeling-toolbox-item)。  
  
若要讓您根據常用的模式輕鬆建立項目或項目群組，您可以將新工具加入 Visual Studio 中的模型圖表工具箱。 您可以將這些工具箱項目散發給其他 Visual Studio 使用者。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 自訂工具會在圖表建立一或多個新項目。 例如，您可以製作自訂工具來建立項目，例如這些項目：  
  
-   連結到 .NET 設定檔的套件，以及包含 .NET 造形的類別。  
  
-   由關聯所連結的一對類別，代表此 [觀察器] 模式。  
  
> [!NOTE]
>  您可以使用這個方法建立項目工具。 也就是說，您可以建立從工具箱拖曳到圖表上的工具。 您無法建立連接器工具。  
  
##  <a name="DefineTool"></a> 定義自訂模型工具  
  
#### <a name="to-define-a-custom-modeling-tool"></a>定義自訂模型工具  
  
1.  建立包含項目或項目群組的 UML 圖表。  
  
    -   這些項目彼此之間可以具有關聯性，也可以擁有子項目，例如通訊埠、屬性、作業或連接。  
  
2.  使用您要指定給新工具的名稱來儲存此圖表。 在 **檔案**功能表上，使用**儲存...為**。  
  
3.  使用 Windows 檔案總管將這兩個圖表檔複製到下列資料夾或任何子資料夾：  
  
     *YourDocuments* **\Visual Studio\Architecture Tools\Custom 工具箱項目**  
  
    -   如果此資料夾尚未存在，請予以建立。 您可能要建立這兩者**架構工具**並**自訂工具箱項目**。  
  
    -   複製這兩個圖表檔，其中"...結束的名稱**圖表**"和結尾的名稱與其他 「...**diagram.layout**"  
  
    -   您可以視需要製作任意數目的自訂工具。 請對於每一項工具使用一個圖表。  
  
4.  （選擇性）建立 **.tbxinfo**檔案中所述[如何定義屬性的自訂工具](#tbxinfo)，並將它加入相同的目錄。 如此可讓您定義工具箱圖示、工具提示等。  
  
    -   單一 **.tbxinfo**檔案可以用來定義數個工具。 它可參考位於子資料夾中的圖表檔。  
  
5.  重新啟動 Visual Studio。 其他工具將在適當類型之圖表的工具箱中出現。  
  
### <a name="what-the-custom-tool-will-replicate"></a>自訂工具將複製的內容  
 自訂工具將複製來源圖表的大部分功能：  
  
-   名稱。 從工具箱建立一個項目時，視需要會在名稱結尾加上一個數字，避免同一個命名空間中出現重複的名稱。  
  
-   色彩、大小和圖形  
  
-   造型和套件設定檔  
  
-   屬性值，例如 Is Abstract  
  
-   連結的工作項目  
  
-   關聯性的多重性和其他屬性  
  
-   圖形的相對位置。  
  
 自訂工具中將不會保留下列功能：  
  
-   簡單圖形。 這些是與模型項目無關的圖形，您可在某些種類的圖表上繪製該模型項目。  
  
-   連接器路由。 如果您手動傳送連接器，則在您使用工具時將不會保留該路由。 某些巢狀圖形 (如連接埠) 的位置並不會相對於其擁有者而予以保留。  
  
##  <a name="tbxinfo"></a> 如何定義自訂工具的屬性  
 工具箱資訊 (**.tbxinfo**) 檔可讓您指定的工具箱名稱、 圖示、 工具提示、 索引標籤上，並說明一或多個自訂工具的關鍵字。 為其指定任何名稱，例如**MyTools.tbxinfo**。  
  
 該檔案的一般形式如下：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">  
  <customToolboxItem fileName="MyObserverTool.classdiagram">  
    <displayName>  
       <value>Observer Pattern</value>  
    </displayName>  
    <tabName>  
       <value>UML Class Diagram</value>  
    </tabName>  
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>  
    <f1Keyword>  
      <value>ObserverPatternHelp</value>  
    </f1Keyword>  
    <tooltip>  
       <value>Create a pair of classes</value>  
    </tooltip>  
  </customToolboxItem>  
</customToolboxItems>  
```  
  
 每一個項目的值可以是：  
  
-   此工具箱圖示的 `<bmp fileName="…"/>` 和其他項目的 `<value>string</value>`，如範例所示。  
  
 \-或-  
  
-   `<resource fileName="Resources.dll"`  
  
     `baseName="Observer.resources" id="Observer.tabname" />`  
  
     在此情況下，您會提供編譯的組件，其中此字串值已編譯為資源。  
  
 請針對您要定義的每一個工具箱項目加入 `<customToolboxItem>` 節點。  
  
 中的節點 **.tbxinfo**檔案如下所示。 每一個節點都有預設值。  
  
|節點名稱|定義|  
|---------------|-------------|  
|displayName|此工具箱項目的名稱。|  
|tabName|工作箱索引標籤，其中應顯示該項目。 您可以針對這類圖表指定一般索引標籤的名稱，或是不同的名稱。|  
|影像|點陣圖的位置 (**.bmp**) 必須具有高度和寬度為 16，色彩深度為 24 位元的檔案。|  
|f1Keyword|尋找說明主題的關鍵字。|  
|工具提示|此工具的工具提示。|  
  
 您可以在 Visual Studio 中編輯此點陣圖檔，並且在 [屬性] 視窗中將其高度和寬度設定為 16。  
  
> [!NOTE]
>  如果您嘗試單獨使用圖表檔之後開始使用 .tbxinfo 檔，可能會發現該工具箱內同時包含舊版和新版的工具箱項目。 如果此 .tbxinfo 檔中圖表檔的名稱輸入錯誤，也會發生這種情況。 如果發生這種情況，在 [工具箱] 的捷徑功能表上選擇**重設工具箱**。 自訂的工具箱項目將會消失。 重新啟動 Visual Studio，然後正確的自訂項目將會出現。  
  
##  <a name="Extension"></a> 如何散發 Visual Studio 擴充功能中的工具箱項目  
 您可以將其他的工具箱項目[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]封裝成 Visual Studio 擴充功能 (VSIX) 的使用者。 您可以將命令、設定檔和其他擴充功能封裝到同一個 VSIX 檔。 如需詳細資訊，請參閱 <<c0> [ 部署 Visual Studio 擴充功能](http://go.microsoft.com/fwlink/?LinkId=160780)。  
  
 通常建置 Visual Studio 擴充功能的方式為使用 VSIX 專案範本。 若要執行這項操作，您必須已安裝 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]。  
  
#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>將工具箱項目加入 Visual Studio 擴充功能  
  
1.  [建立並測試一個或多個自訂工具](#DefineTool)。  
  
2.  [建立.tbxinfo 檔](#tbxinfo)，會參考此工具。  
  
3.  開啟現有的 Visual Studio 擴充功能專案。  
  
     \-或-  
  
     定義新的 Visual Studio 擴充功能專案。  
  
    1.  在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。  
  
    2.  在 **新的專案**對話方塊的 **已安裝的範本**，選擇  **Visual C#**，**擴充性**， **VSIX專案**。  
  
4.  將您的工具箱定義加入此專案。 包含 **.tbxinfo**檔案，該圖表檔、 點陣圖檔案，以及任何資源檔案，並確定它們包含在 VSIX 中。  
  
    -   在 [方案總管] 中，在 VSIX 專案的捷徑功能表上選擇**新增**，**現有項目**。 在對話方塊中，將**類型的物件： 所有檔案**。 找出檔案，它們全部選取，然後選擇**新增**。  
  
        > [!NOTE]
        >  在此專案中，您無法在此模型編輯器開啟該圖表檔。  
  
5.  為您剛才加入的所有檔案設定下列屬性。 藉由在 [方案總管] 中選取所有檔案，您可以同時設定其屬性。 小心不要變更此專案中其他檔案的屬性。  
  
     **複製到輸出目錄** = **一律複製**  
  
     **建置動作** = **內容**  
  
     **包含在 VSIX** = **，則為 true**  
  
6.  開啟 **source.extension.vsixmanifest**。 它會在擴充功能資訊清單編輯器中開啟。  
  
7.  底下**中繼資料**，加入自訂工具的描述。  
  
     底下**資產**，選擇**新增**並將欄位在對話方塊中，如下所示：  
  
    -   **型別** = **自訂延伸模組類型**  
  
    -   類型 = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`  
  
        > [!NOTE]
        >  這不是此下拉式清單的其中一個選項。 您必須使用鍵盤將其輸入。  
  
    -   **來源** = **檔案系統上的**。  
  
    -   **路徑**= 您 **.tbxinfo**檔案，例如**MyTools.tbxinfo**  
  
8.  建置專案。  
  
9. **若要確認此擴充功能的有效**，按下 f5 鍵。 Visual Studio 啟動的實驗執行個體。  
  
     在此實驗執行個體中，建立或開啟該相關類型的 UML 圖表。 請確認您的新工具會出現在此工具箱中，並確認它已正確建立項目。  
  
10. **若要取得部署的 VSIX 檔案：** 在 Windows 檔案總管中，開啟資料夾 **.\bin\Debug**或是 **.\bin\Release**尋找 **.vsix**檔案。 這是 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充檔。 可以將該檔案安裝在您的電腦上，也可以傳送給其他 Visual Studio 使用者。  
  
#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>從 Visual Studio 擴充功能安裝自訂工具  
  
1.  在 Windows 檔案總管或 Visual Studio 中開啟此 `.vsix` 檔案。  
  
2.  選擇**安裝**中出現的對話方塊。  
  
3.  若要解除安裝或暫時停用擴充功能，開啟**擴充功能和更新**從**工具**功能表。  
  
## <a name="localization"></a>當地語系化  
 您可以讓擴充功能安裝在另一部電腦上時，以目標電腦的語言顯示工具名稱和工具提示。  
  
#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>提供多種語言的工具版本  
  
1.  建立包含一個或多個自訂工具的 Visual Studio 擴充功能專案。  
  
     在  **.tbxinfo**檔案，請使用資源檔方法定義的工具`displayName`，工具箱`tabName`，和工具提示。 建立其中已定義這些字串的資源檔，將它編譯成組件，並且從 tbxinfo 檔參考該資源檔。  
  
2.  建立其他組件，其中包含擁有其他語言字串的資源檔。  
  
3.  將每一個額外的組件放入資料夾，且該資料夾以此語言的文化特性代碼命名。 例如，將法文版本的組件放入名為的資料夾**fr**。  
  
4.  您應該使用中性文化特性代碼，通常為兩個字母，而不是特定文化特性 (例如 `fr-CA`)。 如需文化特性代碼的詳細資訊，請參閱[CultureInfo.GetCultures 方法](http://go.microsoft.com/fwlink/?LinkId=160782)，以提供完整的文化特性代碼清單。  
  
5.  建置並散發該 Visual Studio 擴充功能。  
  
6.  當擴充功能安裝到另一部電腦上時，使用者當地文化特性的資源檔版本將會自動載入。 如果您尚未提供該使用者文化特性的版本，則會使用預設資源。  
  
 您無法使用這個方法安裝不同版本的原型圖表。 每一次安裝的項目和連接器名稱都會相同。  
  
## <a name="other-toolbox-operations"></a>其他工具箱作業  
 通常在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 中，您可以重新命名工具、移動到不同的工具箱索引標籤和刪除工具，藉此個人化此工具箱。 但是，對於以本主題描述的程序所建立的自訂模型工具，並不會保存這些變更。 當您重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 時，自訂工具將以其定義的名稱和工具箱位置再次出現。  
  
 如果您執行，您的自訂工具此外，就會消失**重設工具箱**命令。 不過，在您重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 之後，這些工具將再次出現。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)



