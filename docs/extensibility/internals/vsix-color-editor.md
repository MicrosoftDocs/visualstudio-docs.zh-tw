---
title: "VSIX 色彩編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7987d2b6d22893e82893755ed76fa5253aeb600c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-color-editor"></a>VSIX 色彩編輯器
Visual Studio 擴充功能色彩編輯器工具可以建立和編輯 Visual Studio 自訂色彩。 此工具也可以產生佈景主題資源的索引鍵，以便可以在程式碼中使用色彩。 此工具可用於進行 Visual Studio 擴充功能的支援佈景主題色彩。 此工具可開啟.pkgdef 和.xml 檔案。 Visual Studio 佈景主題 （.vstheme 檔案） 可供使用 Visual Studio 擴充功能色彩編輯器中將副檔名變更為.xml。 此外，您還可以.vstheme 檔案匯入目前的.xml 檔案。  
  
 ![VSIX 色彩編輯器主圖](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX 色彩編輯器主圖")  
  
 **封裝定義檔**  
  
 封裝定義 (.pkgdef) 檔會定義主題的檔案。 色本身會儲存在佈景主題色彩.xml 檔案，這會編譯成.pkgdef 檔。 .Pkgdef 檔案部署至 Visual Studio 可搜尋的位置，在執行階段，處理和合併在一起，以定義佈景主題。  
  
 **色彩語彙基元**  
  
 色彩語彙基元是由四個項目所組成：  
  
-   **類別名稱：**邏輯群組的一組色彩。 如果已經有想要的 UI 項目或群組的 UI 項目特定的色彩，請使用現有的類別名稱。  
  
-   **語彙基元名稱：**的色彩語彙基元和語彙基元的集合的描述性名稱。 集包含背景和前景 （文字） 的語彙基元名稱，以及其所有的狀態，而且這些應該命名為，讓您輕鬆地識別組和其套用目標的狀態。  
  
-   **色彩值 （或色調）：**所需的每個彩色佈景主題。 一律建立背景和文字色彩值組中。 色彩被成對的背景/前景的因此一律會針對在其繪製的背景色彩可讀取的文字 （前景） 色彩。 這些色彩的連結，並且會在 UI 中一起使用。 背景不適用於文字，如果未定義的前景色彩。  
  
-   **系統色彩名稱：**用於顯示高對比。  
  
## <a name="how-to-use-the-tool"></a>如何使用工具  
 最大的和現有的 Visual Studio 色彩適用時，應該重複使用而不是進行新的。 不過，如果沒有適當的色彩已定義的情況下，自訂色彩應該建立好相容延伸佈景主題。  
  
 **建立新的色彩語彙基元**  
  
 若要建立使用 Visual Studio 擴充功能色彩編輯器的自訂色彩，請遵循下列步驟：  
  
1.  決定新的色彩語彙基元的類別目錄和語彙基元名稱。  
  
2.  選擇 UI 項目將高對比中對每個主題和系統色彩的色調。  
  
3.  您可以使用 色彩編輯器來建立新的色彩語彙基元。  
  
4.  在 Visual Studio 擴充功能中使用的色彩。  
  
5.  在 Visual Studio 中測試的變更。  
  
 **步驟 1： 決定類別目錄和新的色彩語彙基元的語彙基元名稱。**  
  
 VSColor 是慣用的命名配置**[Category] [UI 型別] [State]**。 重複，所以，請勿 VSColor 名稱中使用的單字 [色彩]。  
  
 分類的名稱提供邏輯群組，而且應定義為範圍狹窄越好。 比方說，單一工具視窗的名稱可能是類別名稱，但不是整個商務單位或專案小組的名稱。 群組分類的項目有助於避免混淆具有相同名稱的色彩。  
  
 項目類型的情況下或 「 狀態 」 會套用色彩，必須清楚指出語彙基元名稱。 比方說，作用中的資料提示**[UI 型別]**可以命名為"**資料提示方塊**"和**[State]**可以命名為"**Active**，"中產生色彩名稱"**DataTipActive**。 」 由於資料提示文字，必須定義的前景和背景色彩。 藉由使用的背景/前景配對，色彩編輯器會自動建立色彩"**DataTipActive**」 的背景和"**DataTipActiveText**"前景。  
  
 如果 UI 段有只有一個狀態， **[State]**名稱的一部分，則可以省略。 比方說，如果在搜尋方塊有框線，而且沒有任何狀態變更會影響框線的色彩，然後框線的色彩語彙基元的名稱只可"**SearchBoxBorder**。 」  
  
 某些常見的狀態名稱包括：  
  
-   作用中  
  
-   非使用中  
  
-   MouseOver  
  
-   MouseDown  
  
-   已選取  
  
-   已取得焦點  
  
 少數的語彙基元名稱的清單項目控制項的組件的範例包括：  
  
-   ListItem  
  
-   ListItemBorder  
  
-   ListItemMouseOver  
  
-   ListItemMouseOverBorder  
  
-   ListItemSelected  
  
-   ListItemSelectedBorder  
  
-   ListItemDisabled  
  
-   ListItemDisabledBorder  
  
 **步驟 2： 選擇 UI 項目將高對比中對每個主題和系統色彩的色調。**  
  
 Ui 選擇自訂色彩，選取類似現有 UI 項目，並使用它的色彩做為基底。 在方塊的 UI 項目色彩已經歷檢閱和測試，使其將會尋找適當且正常運作，所有的主題。  
  
 **步驟 3： 使用色彩編輯器來建立新的色彩語彙基元。**  
  
 啟動色彩編輯器並開啟或建立新的自訂佈景主題色彩.xml 檔案。 選取**編輯 > 新的色彩**從功能表。 這樣會開啟對話方塊，可指定類別目錄和一個或多個名稱為該分類中的色彩項目：  
  
 ![VSIX 色彩編輯器的新色彩](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX 色彩編輯器的新色彩")  
  
 選取現有的類別，或選取**新分類**来建立新的類別。 隨即會開啟另一個對話方塊，建立新的類別名稱：  
  
 ![VSIX 色彩編輯器的新分類](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX 色彩編輯器的新分類")  
  
 新的類別目錄的可用在**新色彩**類別目錄下拉式選單。 後選擇 類別目錄，輸入每個新的色彩語彙基元每行一個名稱，然後選取 建立 完成時：  
  
 ![VSIX 色彩編輯器的新色彩填滿](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX 色彩編輯器的新色彩填滿")  
  
 色彩值會顯示在背景/前景配對，"None"，表示未定義的色彩。 注意： 如果色彩並沒有文字色彩背景色彩配對，然後只在背景，必須定義。  
  
 ![VSIX 色彩編輯器色彩值](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX 色彩編輯器色彩值")  
  
 若要編輯色彩語彙基元，請選取該語彙基元的佈景主題 （資料行） 的色彩項目。 加入色彩值 8 位數 ARGB 格式輸入的十六進位色彩值、 系統色彩名稱輸入資料格，或使用下拉式功能表來選取想要的色彩，透過一組色彩滑桿或系統色彩的清單。  
  
 ![VSIX 色彩編輯器編輯色彩](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX 色彩編輯器編輯色彩")  
  
 ![VSIX 色彩編輯器的背景](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX 色彩編輯器的背景")  
  
 若要顯示的文字不需要的元件，輸入 只有一個色彩值： 背景色彩。 否則，請輸入的背景和文字色彩，以斜線分隔的值。  
  
 當輸入值的高對比，請輸入有效的 Windows 系統色彩名稱。 請勿輸入硬式編碼 ARGB 值。 您可以從色彩值下拉式功能表中選取 「 背景:: 系統 」 或 「 前景:: 系統 」 來檢視有效的系統色彩名稱清單。 建立時具有文字元件的項目，請使用正確的背景文字系統色彩配對或文字可能無法讀取。  
  
 當您完成建立、 設定，以及編輯的色彩語彙基元時，請將它們儲存到所需的.xml 或.pkgdef 格式。 沒有背景的色彩語彙基元也不會另存為.xml 格式的空白色彩但捨棄.pkgdef 格式前景組。 對話方塊會警告您遺失的色彩，如果您嘗試將空的色彩儲存至.pkgdef 檔。  
  
 **步驟 4： 在 Visual Studio 擴充功能中使用的色彩。**  
  
 定義新的色彩後權杖，與 [建置動作] 設為 [內容]，專案檔中包含.pkgdef 和 」 包含在 VSIX 」 設定為"True"。  
  
 ![VSIX 色彩編輯器 pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX 色彩編輯器 pkgdef")  
  
 在 Visual Studio 擴充功能色彩編輯器中，選擇 檔案 > 檢視，檢視用來存取自訂的程式碼的資源程式碼以 WPF 為基礎的 UI 中的色彩。  
  
 ![VSIX 色彩編輯器的資源程式碼檢視器](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX 色彩編輯器的資源程式碼檢視器")  
  
 在專案中的靜態類別中包括此程式碼。 若要參考**Microsoft.VisualStudio.Shell。\<VSVersion >.0.dll**必須加入至專案，以使用**ThemeResourceKey**型別。  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 這可讓您存取 XAML 程式碼中的色彩，並可讓 UI，以回應佈景主題變更。  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **步驟 5： 在 Visual Studio 中測試的變更。**  
  
 色彩編輯器可以暫時將色彩語彙基元適用於 Visual Studio 來檢視即時變更色彩，而不需重建擴充套件的執行個體。 若要這樣做，請按一下"將此佈景主題套用至執行中的 Visual Studio 視窗 」 按鈕位於每個主題的資料行的標頭。 VSIX 色彩編輯器關閉後，這個暫存的佈景主題就會消失運作。  
  
 ![VSIX 色彩編輯器的套用](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX 色彩編輯器的套用")  
  
 若要進行永久變更，重建並重新部署 Visual Studio 擴充功能之後，將新的色彩加入至.pkgdef 檔和寫入的程式碼，將會使用這些色彩。 重建 Visual Studio 擴充功能，會將新的色彩的登錄值合併到其餘的佈景主題。 然後再重新啟動 Visual Studio、 檢視 UI，並確認新的色彩會如預期顯示。  
  
## <a name="notes"></a>注意  
 此工具會用來建立自訂色彩預先存在的 Visual Studio 佈景主題，或編輯自訂 Visual Studio 佈景主題色彩。 若要建立完整的自訂 Visual Studio 佈景主題，請下載[Visual Studio 色彩佈景主題編輯器延伸模組](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b)Visual Studio 擴充功能的組件庫。  
  
## <a name="sample-output"></a>範例輸出  
 **XML 色彩輸出**  
  
 工具所產生的.xml 檔案將會如下所示：  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **PKGDEF 色彩輸出**  
  
 由工具產生.pkgdef 檔將會如下所示：  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **C# 資源金鑰包裝函式**  
  
 由工具產生的色彩資源索引鍵會是如下所示：  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **WPF 資源字典包裝函式**  
  
 色彩**ResourceDictionary**工具所產生的索引鍵會是如下所示：  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```