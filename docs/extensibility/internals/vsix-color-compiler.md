---
title: VSIX 顏色編譯器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703894"
---
# <a name="vsix-color-compiler"></a>VSIX 色彩編譯器
Visual Studio 擴充顏色編譯器工具是一個主控台應用程式,它採用一個表示現有 Visual Studio 主題顏色的 .xml 檔,並將其隱藏到 .pkgdef 檔案中,以便這些顏色可以在 Visual Studio 中使用。 由於很容易比較 .xml 檔案之間的差異,此工具可用於管理原始程式碼管理中的自定義顏色。 還可以將其連接到生成環境,以便生成的輸出是有效的 .pkgdef 檔。

 **主題 XML 架構**

 完整的主題 .xml 檔案如下所示:

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

 \<主題>元素定義整個主題。 主題必須至少包含一個\<類別>元素。 主題元素的定義如下:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**屬性**|**定義**|
|名稱|[ 必需]主題名稱|
|GUID|[ 必需]主題的 GUID(必須符合 GUID 格式)|

 為 Visual Studio 創建自訂顏色時,需要為以下主題定義這些顏色。 如果特定主題不存在顏色,Visual Studio 會嘗試從「燈光」主題載入缺失的顏色。

|||
|-|-|
|**主題名稱**|**主題 GUID**|
|淡|[de3dbbcd-f642-433c-8353-8f1df4370aba]|
|深色|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|藍色|[a4d6a176-b948-4b29-8c66-53c97a1ed7d0]|
|高對比|[a4d6a176-b948-4b29-8c66-53c97a1ed7d0]|

 **類別目錄**

 類別\<>元素定义主题中的颜色集合。 類別名稱提供邏輯分組,並且應盡可能狹義地定義。 類別必須至少包含一個\<顏色>元素。 類別元素的定義如下:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**屬性**|**定義**|
|名稱|[ 必需]類別的名稱|
|GUID|[ 必需]類別的 GUID(必須符合 GUID 格式)|

 **Color**

 顏色\<>元素定义 UI 的元件或狀態的顏色。 顏色的首選命名方案是 [UI 類型] [狀態]。 不要使用"顏色"一詞,因為它是多餘的。 顏色應清楚地指示要應用顏色的元素類型和情況或" 顏色不能為空,並且必須包含\<背景>和\<前景>元素的一個或兩個。 顏色元素的定義如下:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**屬性**|**定義**|
|名稱|[ 必需]顏色的名稱|

 **背景與/或前景**

 背景\<\<>和 前景>元素為 UI 元素的背景或前景定義顏色的值和類型。 這些元素沒有子元素。

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**屬性**|**定義**|
|類型|[ 必需]顏色的類型。 可以是下列其中一項：<br /><br /> *CT_INVALID:* 顏色無效或未設置。<br /><br /> *CT_RAW:* 原始 ARGB 值。<br /><br /> *CT_COLORINDEX:* 請勿使用。<br /><br /> *CT_SYSCOLOR:* 來自 SysColor 的 Windows 系統顏色。<br /><br /> *CT_VSCOLOR:*__VSSYSCOLOREX的視覺工作室顏色。<br /><br /> *CT_AUTOMATIC:* 自動顏色。<br /><br /> *CT_TRACK_FOREGROUND:* 請勿使用。<br /><br /> *CT_TRACK_BACKGROUND:* 請勿使用。|
|來源|[ 必需]十六進位表示的顏色值|

 __VSCOLORTYPE枚舉支援的所有值都由 Type 屬性中的架構支援。 但是,我們建議您僅使用CT_RAW和CT_SYSCOLOR。

 **一起**

 這是一個有效主題 .xml 檔案的簡單範例:

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

## <a name="how-to-use-the-tool"></a>如何使用該工具
 **語法**

 VsixColor編譯器\<XML檔> \<PkgDef\<檔案>可選 Args>

 **引數**

||||
|-|-|-|
|**切換名稱**|**注意**|**必要或選擇**|
|未命名 (.xml 檔案)|這是第一個未命名的參數,是要轉換的 XML 檔的路徑。|必要|
|未命名(.pkgdef 檔案)|這是第二個未命名的參數,是生成的 .pkgdef 檔的輸出路徑。<br /><br /> 預設值:XML\<檔名>.pkgdef|選用|
|/noLogo|設置此標誌將停止列印產品和版權資訊。|選用|
|/?|列印説明資訊。|選用|
|/help|列印説明資訊。|選用|

 **範例**

- VsixColor 編譯器 D:\xml_顏色.xml D:\pkgdef_colors.pkgdef

- VsixColor 編譯器 D:\xml_顏色.xml/noLogo

## <a name="notes"></a>注意

- 此工具要求安裝最新版本的 VC++ 運行時。

- 僅支援單個檔。 不支援通過資料夾路徑進行批量轉換。

## <a name="sample-output"></a>範例輸出
 該工具產生的 .pkgdef 檔案會類似於以下鍵:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
