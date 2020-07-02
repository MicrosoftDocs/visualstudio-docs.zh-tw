---
title: VSIX 色彩編譯器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5059a15c483f648c2248321c7ba8271a634d0c69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536093"
---
# <a name="vsix-color-compiler"></a>VSIX 色彩編譯器
Visual Studio 延伸模組色彩編譯器工具是一個主控台應用程式，它會採用代表現有 Visual Studio 主題色彩的 .xml 檔案，並將其將為 .pkgdef 檔案，讓這些色彩可以用於 Visual Studio。 因為比較 .xml 檔案間的差異很容易，所以這項工具對於管理原始檔控制中的自訂色彩很有用。 它也可以連結到組建環境，讓組建的輸出是有效的 .pkgdef 檔案。

 **主題 XML 架構**

 完整的主題 .xml 檔案看起來像這樣：

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **佈景主題**

 \<Theme>元素會定義整個主題。 主題必須包含至少一個 \<Category> 元素。 主題元素的定義如下：

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**屬性**|**[定義]**|
|-|-|
|名稱|具備主題的名稱|
|GUID|具備主題的 GUID （必須符合 GUID 格式）|

 建立 Visual Studio 的自訂色彩時，必須為下列主題定義這些色彩。 如果特定主題沒有色彩存在，Visual Studio 會嘗試從淺色主題載入遺漏的色彩。

|**主題名稱**|**主題 GUID**|
|-|-|
|淺色|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|深色|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|藍色|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|高對比|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **類別**

 \<Category>元素會定義主題中的色彩集合。 類別目錄名稱會提供邏輯群組，而且應該盡可能地定義為最窄。 分類必須包含至少一個 \<Color> 元素。 Category 元素的定義如下：

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**屬性**|**[定義]**|
|-|-|
|名稱|具備類別目錄的名稱|
|GUID|具備類別的 GUID （必須符合 GUID 格式）|

 **色彩**

 \<Color>元素會定義元件或 UI 狀態的色彩。 色彩慣用的命名配置為 [UI 類型] [狀態]。 請勿使用「色彩」一詞，因為它是多餘的。 色彩應該會清楚地指出要套用色彩的元素類型和狀況，或「狀態」。 色彩不得為空白，且必須包含一個或兩個專案 \<Background> \<Foreground> 。 色彩元素的定義如下：

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**屬性**|**[定義]**|
|-|-|
|名稱|具備色彩的名稱|

 **背景和/或前景**

 \<Background>和 \<Foreground> 元素會針對 UI 專案的背景或前景，定義色彩的值和類型。 這些元素沒有子系。

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**屬性**|**[定義]**|
|-|-|
|類型|具備色彩的類型。 可以是下列其中一項：<br /><br /> *CT_INVALID：* 色彩無效或未設定。<br /><br /> *CT_RAW：* 原始 ARGB 值。<br /><br /> *CT_COLORINDEX：* 請勿使用。<br /><br /> *CT_SYSCOLOR：* 來自 SysColor 的 Windows 系統色彩。<br /><br /> *CT_VSCOLOR：*__VSSYSCOLOREX 的 Visual Studio 色彩。<br /><br /> *CT_AUTOMATIC：* 自動色彩。<br /><br /> *CT_TRACK_FOREGROUND：* 請勿使用。<br /><br /> *CT_TRACK_BACKGROUND：* 請勿使用。|
|來源|具備以十六進位表示的色彩值|

 Type 屬性中的架構支援 __VSCOLORTYPE 列舉所支援的所有值。 不過，我們建議您只使用 CT_RAW 和 CT_SYSCOLOR。

 **全部整合**

 這是有效的主題 .xml 檔案的簡單範例：

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>如何使用工具
 **語法**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **引數**

|**交換器名稱**|**備註**|**Required 或 Optional**|
|-|-|-|
|未命名的（.xml 檔案）|這是第一個未命名的參數，而是要轉換之 XML 檔案的路徑。|必要|
|未命名（. .pkgdef 檔案）|這是第二個未命名的參數，而是所產生 .pkgdef 檔案的輸出路徑。<br /><br /> 預設值： \<XML Filename> . .pkgdef|選擇性|
|/noLogo|設定此旗標會阻止產品和著作權資訊進行列印。|選擇性|
|/?|印出說明資訊。|選擇性|
|/help|印出說明資訊。|選用|

 **範例**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>注意

- 此工具需要安裝最新版本的 VC + + 執行時間。

- 僅支援單一檔案。 不支援透過資料夾路徑進行大量轉換。

## <a name="sample-output"></a>範例輸出
 此工具所產生的 .pkgdef 檔案會類似以下的機碼：

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
