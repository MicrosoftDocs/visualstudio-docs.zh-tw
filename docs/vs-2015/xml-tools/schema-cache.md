---
title: 架構快取 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d590bf618693a5ced1aa17969b888c0fff130c4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476952"
---
# <a name="schema-cache"></a>結構描述快取
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器提供位於 %InstallRoot%\Xml\Schemas 目錄中的結構描述快取。 結構描述快取對於您電腦上的所有使用者都是通用的，它包括用於 IntelliSense 及 XML 文件驗證的標準 XML 結構描述。

 XML 編輯器也可以尋找位於方案中的架構、[檔**屬性**] 視窗的 [**架構**] 欄位中指定的架構，以及和屬性所識別的架構 `xsi:schemaLocation` `xsi:noNamespaceSchemaLocation` 。

 下表說明隨 XML 編輯器安裝的結構描述。

|     檔案名稱      |                                                      描述                                                      |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
|    catalog.xsd    |             XML 編輯器結構描述目錄檔案的結構描述。 如需結構描述目錄的詳細資訊，請參閱下方。             |
| DotNetConfig.xsd  |                 Web.Config 檔案的架構 `http://schemas.microsoft.com/.NETConfiguration/v2.0` 。                 |
|    msbuild.xsd    |              MSBuild 製作檔案的架構 `http://schemas.microsoft.com/developer/msbuild/2003` 。              |
|    msdata.xsd     | <xref:System.Data.DataSet> 類別所加入之 XSD 附註的結構描述 urn:schemas-microsoft-com:xml-msdata。 |
|     msxsl.xsd     |                  Microsoft XSLT 指令碼區塊擴充程式的結構描述 urn:schemas-microsoft-com:xslt。                   |
| SnippetFormat.xsd |                 程式碼片段 XML 檔案的結構描述。 例如，請參閱 %InstallDir%\VC#\Expansions。                 |
|    Soap1.1.xsd    |            簡易物件存取通訊協定的架構 (SOAP) 1.1 `http://schemas.xmlsoap.org/soap/envelope/` 。            |
|    Soap1.2.xsd    |                                     簡易物件存取通訊協定 1.2 的結構描述。                                     |
| SiteMapSchema.xsd |            ASP.NET 網站地圖 XML 檔案的架構 `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0` 。             |
|     wsdl.xsd      |                    Web 服務描述語言的架構 `http://schemas.xmlsoap.org/wsdl/` 。                     |
|     xenc.xsd      |                            XML 加密的架構 `http://www.w3.org/2000/09/xmldsig#` 。                             |
|     xhtml.xsd     |                                    XHTML 的架構 `http://www.w3.org/1999/xhtml` 。                                     |
|     xlink.xsd     |                                  XLink 1.0 的架構 `http://www.w3.org/1999/xlink` 。                                   |
|      xml.xsd      |              描述 xml： space 和 xml： lang 屬性的架構 `http://www.w3.org/XML/1998/namespace` 。               |
|    xmlsig.xsd     |                        XML 數位簽章的架構 `http://www.w3.org/2000/09/xmldsig#` 。                         |
|   xsdschema.xsd   |                            描述 XSD 本身的架構 `http://www.w3.org/2001/XMLSchema` 。                            |
|     xslt.xsd      |                           XML 轉換的架構 `http://www.w3.org/1999/XSL/Transform` 。                            |

## <a name="updating-schemas-in-the-cache"></a>更新快取中的結構描述
 編輯器會在載入 XML 編輯器封裝時，載入結構描述快取目錄，並於執行期間監看是否發生任何變更。 如果已加入結構描述，則會將其自動載入已知結構描述的記憶體中索引。 如果已移除結構描述，則會將其自動從記憶體中索引移除。 如果已更新結構描述，則會自動讓此結構描述的記憶體中快取失效。

> [!NOTE]
> 因為結構描述快取目錄對您的電腦是通用的，所以在這裡您應該僅加入標準的、且對您電腦上可能建立之所有 Visual Studio 專案皆有用的結構描述。

 XML 編輯器亦支援結構描述快取目錄中任意數目的結構描述目錄檔案。 結構描述目錄可指向您通常想要編輯器瞭解之結構描述的其他位置。 catalog.xsd 檔定義目錄檔案的格式，並包含在結構描述快取目錄中。 catalog.xml 檔是預設的目錄，而且包含 %InstallDir% 中其他結構描述的連結。 以下是 catalog.xml 檔的範例：

```
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

 `href` 屬性可以是指向結構描述的任意檔案路徑或 http URL。 檔案路徑是對目錄文件的相對路徑。 編輯器會辨識以 %% 分隔的下列變數，並在路徑中展開它們：

- InstallDir

- 系統

- ProgramFiles

- 程式

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

  目錄文件可包含指向其他目錄的 `Catalog` 項目。 您可以使用 `Catalog` 項目指向小組或公司共用的中心目錄，或與業務夥伴共用的線上目錄。 `href` 屬性是其他目錄的檔案路徑或 http URL。 以下是 `Catalog` 項目的範例：

```
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

 目錄還可以使用特殊的 `Association` 項目，來控制結構描述如何與 XML 文件產生關聯。 此項目將沒有目標命名空間的結構描述與特定的副檔名相關聯，這樣做很有用，因為 XML 編輯器不會自動關聯任何沒有 `targetNamespace` 屬性的結構描述。 在下列範例中，`Association` 項目將 dotNetConfig 結構描述，與具有 config 副檔名的所有檔案相關聯：

```
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>當地語系化結構描述
 在許多情況下，catalog.xml 檔不包含當地語系化結構描述的項目。 您可以將其他項目加入到指向當地語系化資料結構目錄的 catalog.xml 檔案中。

 在下列範例中，已經建立使用 %LCID% 變數指向當地語系化結構描述的新 `Schema` 項目。

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="changing-the-location-of-the-schema-cache"></a>變更結構描述快取的位置
 您可以使用 [ **其他** 選項] 頁面自訂架構快取的位置。 如果您有偏好之結構描述的目錄，則可以設定編輯器改為使用那些結構描述。

> [!NOTE]
> 此變更僅會影響目前的 Visual Studio 使用者。

#### <a name="to-change-the-schema-cache-location"></a>變更結構描述快取位置

1. 請從 [工具] 功能表上，選取 [選項]。

2. 展開 [ **文字編輯器**]，展開 [ **XML**]，然後按一下 [ **其他**]。

3. 按一下 [**架構**] 欄位上的 [**流覽]** 按鈕。

4. 選取架構快取的資料夾，然後按一下 **[確定]**。

#### <a name="to-add-another-directory-of-common-schemas"></a>加入通用結構描述的其他目錄

1. 編輯 XML 編輯器結構描述快取目錄中的 catalog.xml 檔。

2. 加入指向其他結構描述目錄的新 `<Catalog href="…"/>` 項目。

3. 儲存您的變更。

     目錄會自動重新載入。

## <a name="see-also"></a>另請參閱
 [XML 編輯器](../xml-tools/xml-editor.md)
