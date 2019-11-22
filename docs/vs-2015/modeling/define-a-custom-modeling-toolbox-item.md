---
title: 定義自訂模型工具箱專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac299f18e544ef4f3215707abbdc3d9e8d266de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299297"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>定義自訂模型工具箱項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要讓您根據常用的模式輕鬆建立項目或項目群組，您可以將新工具加入 Visual Studio 中的模型圖表工具箱。 您可以將這些工具箱項目散發給其他 Visual Studio 使用者。

 若要查看哪些版本的 Visual Studio 支援此功能，請參閱 [Architecture and Modeling Tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

 自訂工具會在圖表建立一或多個新項目。 例如，您可以製作自訂工具來建立項目，例如這些項目：

- 連結到 .NET 設定檔的套件，以及包含 .NET 造形的類別。

- 由關聯所連結的一對類別，代表此 [觀察器] 模式。

> [!NOTE]
> 您可以使用這個方法建立項目工具。 也就是說，您可以建立從工具箱拖曳到圖表上的工具。 您無法建立連接器工具。

## <a name="DefineTool"></a>定義自訂模型工具

#### <a name="to-define-a-custom-modeling-tool"></a>定義自訂模型工具

1. 建立包含項目或項目群組的 UML 圖表。

    - 這些項目彼此之間可以具有關聯性，也可以擁有子項目，例如通訊埠、屬性、作業或連接。

2. 使用您要指定給新工具的名稱來儲存此圖表。 請使用 [檔案] 功能表上的 [另存為...]。

3. 使用 Windows 檔案總管將這兩個圖表檔複製到下列資料夾或任何子資料夾：

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom 工具箱專案**

    - 如果此資料夾尚未存在，請予以建立。 您可能必須建立**架構工具**和**自訂工具箱專案**。

    - 複製這兩個圖表檔案，一個名稱結尾為 "..." 的檔案。[**圖表**]，另一個名稱結尾為 "。[**圖表]。版面**配置 "

    - 您可以視需要製作任意數目的自訂工具。 請對於每一項工具使用一個圖表。

4. 選擇性如[如何定義自訂工具的屬性](#tbxinfo)中所述，建立 **.tbxinfo**檔案，並將它新增至相同的目錄。 如此可讓您定義工具箱圖示、工具提示等。

    - 您可以使用單一 **.tbxinfo**檔案來定義數個工具。 它可參考位於子資料夾中的圖表檔。

5. 重新啟動 Visual Studio。 其他工具將在適當類型之圖表的工具箱中出現。

### <a name="what-the-custom-tool-will-replicate"></a>自訂工具將複製的內容
 自訂工具將複製來源圖表的大部分功能：

- 名稱。 從工具箱建立一個項目時，視需要會在名稱結尾加上一個數字，避免同一個命名空間中出現重複的名稱。

- 色彩、大小和圖形

- 造型和套件設定檔

- 屬性值，例如 Is Abstract

- 連結的工作項目

- 關聯性的多重性和其他屬性

- 圖形的相對位置。

  自訂工具中將不會保留下列功能：

- 簡單圖形。 這些是與模型項目無關的圖形，您可在某些種類的圖表上繪製該模型項目。

- 連接器路由。 如果您手動傳送連接器，則在您使用工具時將不會保留該路由。 某些巢狀圖形 (如連接埠) 的位置並不會相對於其擁有者而予以保留。

## <a name="tbxinfo"></a>如何定義自訂工具的屬性
 [工具箱資訊] （ **. .tbxinfo**）檔案可讓您指定一個或多個自訂工具的工具箱名稱、圖示、工具提示、索引標籤和說明關鍵字。 為它命名，例如**MyTools. .tbxinfo**。

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

- 此工具箱圖示的 `<bmp fileName="…"/>` 和其他項目的 `<value>string</value>`，如範例所示。

  \-或-

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   在此情況下，您會提供編譯的組件，其中此字串值已編譯為資源。

  請針對您要定義的每一個工具箱項目加入 `<customToolboxItem>` 節點。

  **.Tbxinfo**檔案中的節點如下所示。 每一個節點都有預設值。

|節點名稱|定義|
|---------------|-------------|
|displayName|此工具箱項目的名稱。|
|tabName|工作箱索引標籤，其中應顯示該項目。 您可以針對這類圖表指定一般索引標籤的名稱，或是不同的名稱。|
|影像|點陣圖（ **.bmp**）檔案的位置，其高度和寬度必須為16，而色彩深度為24位。|
|f1Keyword|尋找說明主題的關鍵字。|
|工具提示|此工具的工具提示。|

 您可以在 Visual Studio 中編輯此點陣圖檔，並且在 [屬性] 視窗中將其高度和寬度設定為 16。

> [!NOTE]
> 如果您嘗試單獨使用圖表檔之後開始使用 .tbxinfo 檔，可能會發現該工具箱內同時包含舊版和新版的工具箱項目。 如果此 .tbxinfo 檔中圖表檔的名稱輸入錯誤，也會發生這種情況。 如果發生這種情況，請在該工具箱的捷徑功能表中選擇 [重設工具箱]。 自訂的工具箱項目將會消失。 重新啟動 Visual Studio，然後正確的自訂項目將會出現。

## <a name="Extension"></a>如何散發 Visual Studio 延伸模組中的工具箱專案
 您可以將工具箱專案封裝成 Visual Studio 延伸模組（VSIX），以將它們散發給其他 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用者。 您可以將命令、設定檔和其他擴充功能封裝到同一個 VSIX 檔。 如需詳細資訊，請參閱[部署 Visual Studio 延伸](https://go.microsoft.com/fwlink/?LinkId=160780)模組。

 通常建置 Visual Studio 擴充功能的方式為使用 VSIX 專案範本。 若要執行這項操作，您必須已安裝 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]。

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>將工具箱項目加入 Visual Studio 擴充功能

1. [建立及測試一或多個自訂工具](#DefineTool)。

2. [建立 .tbxinfo 檔](#tbxinfo)，該檔案會參考此工具。

3. 開啟現有的 Visual Studio 擴充功能專案。

     \-或-

     定義新的 Visual Studio 擴充功能專案。

    1. 在 [檔案] 功能表上，依序選擇 [新增] 和 [專案]。

    2. 在 [新增專案] 對話方塊中的 [已安裝的範本] 底下，選擇 [Visual C#]、[擴充性]、[VSIX 專案]。

4. 將您的工具箱定義加入此專案。 包含 **.tbxinfo**檔案、圖表檔案、點陣圖檔案和任何資源檔，並確定這些檔案已包含在 VSIX 中。

    - 在 [方案總管] 中的 VSIX 專案捷徑功能表上，選擇 [加入]、[現有項目]。 在此對話方塊中，設定 [類型的物件: 所有檔案]。 尋找此檔案，將它們全部選取，然後選擇 [加入]。

        > [!NOTE]
        > 在此專案中，您無法在此模型編輯器開啟該圖表檔。

5. 為您剛才加入的所有檔案設定下列屬性。 藉由在 [方案總管] 中選取所有檔案，您可以同時設定其屬性。 小心不要變更此專案中其他檔案的屬性。

     **複製到輸出目錄** = **一律複製**

      = **內容**的**組建動作**

     **包含在 VSIX** = **true**

6. 開啟 **source.extension.vsixmanifest**。 它會在擴充功能資訊清單編輯器中開啟。

7. 請在 [中繼資料] 下，加入此自訂工具的描述。

     在 [資產] 底下，選擇 [新增]，然後設定此對話方塊中的欄位如下：

    - **輸入** = **自訂延伸模組類型**

    - 類型 = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > 這不是下拉式清單的其中一個選項。 您必須使用鍵盤將其輸入。

    - 檔**系統上的** **來源** = 檔案。

    - **Path** = 您的 **.tbxinfo**檔案，例如**MyTools. .tbxinfo**

8. 建置專案。

9. **若要確認擴充功能是否正常運作**，請按 F5。 Visual Studio 啟動的實驗執行個體。

     在此實驗執行個體中，建立或開啟該相關類型的 UML 圖表。 請確認您的新工具會出現在此工具箱中，並確認它已正確建立項目。

10. **若要取得用於部署的 VSIX 檔案：** 在 Windows Explorer 中，開啟 **.\bin\Debug**或 **.\bin\Release**資料夾，以尋找 **.vsix**檔案。 這是 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充檔。 可以將該檔案安裝在您的電腦上，也可以傳送給其他 Visual Studio 使用者。

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>從 Visual Studio 擴充功能安裝自訂工具

1. 在 Windows 檔案總管或 Visual Studio 中開啟此 `.vsix` 檔案。

2. 在出現的對話方塊中選擇 [安裝]。

3. 若要解除安裝或暫時停用此擴充功能，請從 [工具] 功能表開啟 [擴充功能和更新]。

## <a name="localization"></a>當地語系化
 您可以讓擴充功能安裝在另一部電腦上時，以目標電腦的語言顯示工具名稱和工具提示。

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>提供多種語言的工具版本

1. 建立包含一個或多個自訂工具的 Visual Studio 擴充功能專案。

    在 **.tbxinfo**檔案中，使用資源檔方法來定義工具的 `displayName`、工具箱 `tabName`和工具提示。 建立其中已定義這些字串的資源檔，將它編譯成組件，並且從 tbxinfo 檔參考該資源檔。

2. 建立其他組件，其中包含擁有其他語言字串的資源檔。

3. 將每一個額外的組件放入資料夾，且該資料夾以此語言的文化特性代碼命名。 例如，將法文版的元件放在名為**fr**的資料夾內。

4. 您應該使用中性文化特性代碼，通常為兩個字母，而不是特定文化特性 (例如 `fr-CA`)。 如需文化特性代碼的詳細資訊，請參閱[cultureinfo.getcultures 方法](https://go.microsoft.com/fwlink/?LinkId=160782)，它會提供完整的文化特性代碼清單。

5. 建置並散發該 Visual Studio 擴充功能。

6. 當擴充功能安裝到另一部電腦上時，使用者當地文化特性的資源檔版本將會自動載入。 如果您尚未提供該使用者文化特性的版本，則會使用預設資源。

   您無法使用這個方法安裝不同版本的原型圖表。 每一次安裝的項目和連接器名稱都會相同。

## <a name="other-toolbox-operations"></a>其他工具箱作業
 通常在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 中，您可以重新命名工具、移動到不同的工具箱索引標籤和刪除工具，藉此個人化此工具箱。 但是，對於以本主題描述的程序所建立的自訂模型工具，並不會保存這些變更。 當您重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 時，自訂工具將以其定義的名稱和工具箱位置再次出現。

 除此之外，如果您執行 [重設工具箱] 命令，自訂工具將會消失。 不過，在您重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 之後，這些工具將再次出現。

## <a name="see-also"></a>另請參閱
 [擴充 uml 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)[定義設定檔以擴充 uml](../modeling/define-a-profile-to-extend-uml.md) [在模型圖表上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)[定義 uml 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)
