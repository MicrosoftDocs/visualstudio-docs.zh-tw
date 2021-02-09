---
title: XML 編輯器架構快取
description: 瞭解 XML 編輯器所提供的架構快取，其中包含用於 IntelliSense 和 XML 檔驗證的標準 XML 架構。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3562b7238f9721c4153af02cce594bfb9e134b0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841884"
---
# <a name="schema-cache"></a>結構描述快取

XML 編輯器提供位於 *%VSInstallDir%\xml\Schemas* 目錄中的架構快取。 架構快取對於您電腦上的所有使用者都是通用的，而且包含用於 IntelliSense 和 XML 檔驗證的標準 XML 架構。

XML 編輯器也可以尋找位於方案中的架構、[檔 **屬性**] 視窗的 [**架構**] 欄位中指定的架構，以及和屬性所識別的架構 `xsi:schemaLocation` `xsi:noNamespaceSchemaLocation` 。

下表說明使用 XML 編輯器安裝的架構。

| 檔案名稱 | 描述 |
|-| - |
| *catalog.xsd* | XML 編輯器結構描述目錄檔案的結構描述。 如需結構描述目錄的詳細資訊，請參閱下方。 |
| *DotNetConfig.xsd* | Web.Config 檔案的架構 `http://schemas.microsoft.com/.NETConfiguration/v2.0` 。 |
| *msbuild.xsd* | MSBuild 製作檔案的架構 `http://schemas.microsoft.com/developer/msbuild/2003` 。 |
| *msdata.xsd* | <xref:System.Data.DataSet> 類別所加入之 XSD 附註的結構描述 urn:schemas-microsoft-com:xml-msdata。 |
| *msxsl.xsd* | Microsoft XSLT 指令碼區塊擴充程式的結構描述 urn:schemas-microsoft-com:xslt。 |
| *SnippetFormat.xsd* | 程式碼片段 XML 檔案的結構描述。 如需範例，請參閱 *%VSInstallDir%\VC # \Expansions*。 |
| *Soap1.1.xsd* | 簡易物件存取通訊協定的架構 (SOAP) 1.1 `http://schemas.xmlsoap.org/soap/envelope/` 。 |
| *Soap1.2.xsd* | 簡易物件存取通訊協定 1.2 的結構描述。 |
| *SiteMapSchema.xsd* | ASP.NET 網站地圖 XML 檔案的架構 `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0` 。 |
| *wsdl.xsd* | Web 服務描述語言的架構 `http://schemas.xmlsoap.org/wsdl/` 。 |
| *xenc.xsd* | XML 加密的架構 `http://www.w3.org/2000/09/xmldsig#` 。 |
| *xhtml.xsd* | XHTML 的架構 `http://www.w3.org/1999/xhtml` 。 |
| *xlink.xsd* | XLink 1.0 的架構 `http://www.w3.org/1999/xlink` 。 |
| *xml.xsd* | 描述 xml： space 和 xml： lang 屬性的架構 `http://www.w3.org/XML/1998/namespace` 。 |
| *xmlsig.xsd* | XML 數位簽章的架構 `http://www.w3.org/2000/09/xmldsig#` 。 |
| *xsdschema.xsd* | 描述 XSD 本身的架構 `http://www.w3.org/2001/XMLSchema` 。 |
| *xslt.xsd* | XML 轉換的架構 `http://www.w3.org/1999/XSL/Transform` 。 |

## <a name="update-schemas-in-the-cache"></a>更新快取中的架構

編輯器會在載入 XML 編輯器封裝時，載入結構描述快取目錄，並於執行期間監看是否發生任何變更。 如果已加入結構描述，則會將其自動載入已知結構描述的記憶體中索引。 如果已移除結構描述，則會將其自動從記憶體中索引移除。 如果已更新結構描述，則會自動讓此結構描述的記憶體中快取失效。

> [!NOTE]
> 因為結構描述快取目錄對您的電腦是通用的，所以在這裡您應該僅加入標準的、且對您電腦上可能建立之所有 Visual Studio 專案皆有用的結構描述。

XML 編輯器亦支援結構描述快取目錄中任意數目的結構描述目錄檔案。 結構描述目錄可指向您通常想要編輯器瞭解之結構描述的其他位置。 *Catalog .xsd* 檔會定義目錄檔案的格式，並包含在架構快取目錄中。 *catalog.xml* 檔案是預設目錄，它包含 *% VSInstallDir%* 中其他架構的連結。 以下是 *catalog.xml* 檔案的取樣：

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

`href` 屬性可以是指向結構描述的任意檔案路徑或 http URL。 檔案路徑是對目錄文件的相對路徑。 編輯器會辨識下列變數（以%% 分隔），並在路徑中展開：

- VSInstallDir

- 系統

- ProgramFiles

- 程式

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

目錄文件可包含指向其他目錄的 `Catalog` 項目。 您可以使用 `Catalog` 項目指向小組或公司共用的中心目錄，或與業務夥伴共用的線上目錄。 `href` 屬性是其他目錄的檔案路徑或 http URL。 以下是 `Catalog` 項目的範例：

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

目錄還可以使用特殊的 `Association` 項目，來控制結構描述如何與 XML 文件產生關聯。 這個元素會將沒有目標命名空間的架構與特定的副檔名產生關聯，這會很有用，因為 XML 編輯器不會自動關聯沒有屬性的架構 `targetNamespace` 。 在下列範例中，`Association` 項目將 dotNetConfig 結構描述，與具有 config 副檔名的所有檔案相關聯：

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>當地語系化的架構

在許多情況下， *catalog.xml* 檔案不包含當地語系化架構的專案。 您可以將其他專案新增至指向當地語系化架構目錄的 *catalog.xml* 檔案。

在下列範例中，已經建立使用 %LCID% 變數指向當地語系化結構描述的新 `Schema` 項目。

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>變更架構快取的位置

您可以使用 [ **其他** 選項] 頁面自訂架構快取的位置。 如果您有偏好之結構描述的目錄，則可以設定編輯器改為使用那些結構描述。

> [!NOTE]
> 此變更僅會影響目前的 Visual Studio 使用者。

### <a name="to-change-the-schema-cache-location"></a>變更結構描述快取位置

1. 請從 [工具] 功能表上，選取 [選項]。

2. 展開 [ **文字編輯器**]，展開 [ **XML**]，然後按一下 [ **其他**]。

3. 按一下 [**架構**] 欄位上的 [**流覽]** 按鈕。

4. 選取架構快取的資料夾，然後按一下 **[確定]**。

### <a name="to-add-another-directory-of-common-schemas"></a>加入通用結構描述的其他目錄

1. 編輯 XML 編輯器架構快取目錄中的 *catalog.xml* 檔案。

2. 加入指向其他結構描述目錄的新 `<Catalog href="..."/>` 項目。

3. 儲存您的變更。

   目錄會自動重新載入。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
