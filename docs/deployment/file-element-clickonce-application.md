---
title: '&lt;&gt; (ClickOnce 應用程式) 的 file 元素 |Microsoft Docs'
description: File 元素會識別應用程式下載並使用的所有 nonassembly 檔案。 File 元素是選擇性的。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ad19de19176b7c8ee1d2c2872126a19abb93b67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895085"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;&gt;ClickOnce 應用程式) 的 file 元素 (
識別應用程式下載並使用的所有 nonassembly 檔案。

## <a name="syntax"></a>Syntax

```xml
<file
    name
    size
    group
    optional
    writeableType
>
    <typelib
        tlbid
        version
        helpdir
        resourceid
        flags
    />
    <comClass
        clsid
        description
        threadingModel
        tlbid
        progid
        miscStatus
        miscStatusIcon
        miscStatusContent
        miscStatusDocPrint
        miscStatusThumbnail
    />
    <comInterfaceExternalProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <comInterfaceProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <windowClass
        versioned
    />
</file>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `file` 則是選擇性元素。 元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|必要。 識別檔案的名稱。|
|`size`|必要。 指定檔案的大小（以位元組為單位）。|
|`group`|如果未 `optional` 指定屬性或設定為，則為選擇性 `false` ; 如果為，則為必要項 `optional` `true` 。 這個檔案所屬的組名。 名稱可以是開發人員所選擇的任何 Unicode 字串值，而且會用來依需求以類別下載檔案 <xref:System.Deployment.Application.ApplicationDeployment> 。|
|`optional`|選擇性。 指定當應用程式第一次執行時，此檔案是否必須下載，或者檔案是否應該只存在於伺服器上，直到應用程式視需要要求為止。 如果 `false` 或未定義，則會在第一次執行或安裝應用程式時下載檔案。 如果為 `true` ， `group` 則必須指定，才能讓應用程式資訊清單有效。 `optional` 如果 `writeableType` 以值指定，則不可以是 true `applicationData` 。|
|`writeableType`|選擇性。 指定這個檔案是資料檔案。 目前唯一有效的值是 `applicationData`。|

## <a name="typelib"></a>typelib
 `typelib`元素是 file 元素的選擇性子專案。 元素會描述屬於 COM 元件的類型程式庫。 元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`tlbid`|必要。 指派給類型程式庫的 GUID。|
|`version`|必要。 類型程式庫的版本號碼。|
|`helpdir`|必要。 包含元件說明檔的目錄。 可能為零長度。|
|`resourceid`|選擇性。 地區設定識別碼的十六進位字串標記法 (LCID) 。 這是一到四個十六進位數位，沒有0x 前置詞且沒有前置零。 LCID 可能具有中性的子語言識別項。|
|`flags`|選擇性。 此類型程式庫之類型程式庫旗標的字串表示。 具體而言，它應該是「受限」、「控制」、「隱藏」和「HASDISKIMAGE」其中一個。|

## <a name="comclass"></a>comClass
 專案 `comClass` 是專案的選擇性子系 `file` ，但如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式包含其打算使用免註冊 com 來部署的 COM 元件，則為必要專案。 元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`clsid`|必要。 以 GUID 表示之 COM 元件的類別識別碼。|
|`description`|選擇性。 類別名稱。|
|`threadingModel`|選擇性。 同進程 COM 類別所使用的執行緒模型。 如果此屬性為 null，則不會使用任何執行緒模型。 元件是在用戶端的主執行緒上建立，而來自其他執行緒的呼叫會封送處理至此執行緒。 下列清單顯示有效的值：<br /><br /> `Apartment`、`Free`、`Both` 和 `Neutral`。|
|`tlbid`|選擇性。 此 COM 元件之類型程式庫的 GUID。|
|`progid`|選擇性。 與 COM 元件相關聯的版本相依程式設計識別碼。 的格式 `ProgID` 為 `<vendor>.<component>.<version>` 。|
|`miscStatus`|選擇性。 組件資訊清單中的重複專案會提供登錄機碼所提供的資訊 `MiscStatus` 。 如果 `miscStatusIcon` 找不到、 `miscStatusContent` 、 `miscStatusDocprint` 或屬性的值，則 `miscStatusThumbnail` 會使用中所列的對應預設值 `miscStatus` 做為遺漏的屬性。 值可以是下表中的屬性值清單（以逗號分隔）。 如果 COM 類別是需要登錄機碼值的 OCX 類別，您可以使用這個屬性 `MiscStatus` 。|
|`miscStatusIcon`|選擇性。 組件資訊清單中的重複專案，DVASPECT_ICON 提供的資訊。 它可以提供物件的圖示。 值可以是下表中的屬性值清單（以逗號分隔）。 如果 COM 類別是需要登錄機碼值的 OCX 類別，您可以使用這個屬性 `Miscstatus` 。|
|`miscStatusContent`|選擇性。 組件資訊清單中的重複專案，DVASPECT_CONTENT 提供的資訊。 它可以為螢幕或印表機提供可顯示的複合檔案。 值可以是下表中的屬性值清單（以逗號分隔）。 如果 COM 類別是需要登錄機碼值的 OCX 類別，您可以使用這個屬性 `MiscStatus` 。|
|`miscStatusDocPrint`|選擇性。 組件資訊清單中的重複專案，DVASPECT_DOCPRINT 提供的資訊。 它可以提供在螢幕上顯示的物件標記法，就像列印到印表機一樣。 值可以是下表中的屬性值清單（以逗號分隔）。 如果 COM 類別是需要登錄機碼值的 OCX 類別，您可以使用這個屬性 `MiscStatus` 。|
|`miscStatusThumbnail`|選擇性。 組件資訊清單中的重複專案，DVASPECT_THUMBNAIL 提供的資訊。 它可以提供流覽工具中可顯示物件的縮圖。 值可以是下表中的屬性值清單（以逗號分隔）。 如果 COM 類別是需要登錄機碼值的 OCX 類別，您可以使用這個屬性 `MiscStatus` 。|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 專案 `comInterfaceExternalProxyStub` 是專案的選擇性子系 `file` ，但如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式包含要使用免註冊的 com 來部署的 COM 元件，則可能需要此元素。 元素包含下列屬性。

|屬性|描述|
|---------------|-----------------|
|`iid`|必要。 由此 proxy 提供的 (IID) 介面識別碼。 IID 必須有括弧括住。|
|`baseInterface`|選擇性。 所參考之介面衍生來源介面的 IID `iid` 。|
|`numMethods`|選擇性。 介面所執行的方法數目。|
|`name`|選擇性。 在程式碼中會出現的介面名稱。|
|`tlbid`|選擇性。 類型程式庫，其中包含屬性所指定之介面的描述 `iid` 。|
|`proxyStubClass32`|選擇性。 將 IID 對應至32位 proxy Dll 中的 CLSID。|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 專案 `comInterfaceProxyStub` 是專案的選擇性子系 `file` ，但如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式包含要使用免註冊的 com 來部署的 COM 元件，則可能需要此元素。 元素包含下列屬性。

|屬性|描述|
|---------------|-----------------|
|`iid`|必要。 由此 proxy 提供的 (IID) 介面識別碼。 IID 必須有括弧括住。|
|`baseInterface`|選擇性。 所參考之介面衍生來源介面的 IID `iid` 。|
|`numMethods`|選擇性。 介面所執行的方法數目。|
|`Name`|選擇性。 在程式碼中會出現的介面名稱。|
|`Tlbid`|選擇性。 類型程式庫，其中包含屬性所指定之介面的描述 `iid` 。|
|`proxyStubClass32`|選擇性。 將 IID 對應至32位 proxy Dll 中的 CLSID。|
|`threadingModel`|選擇性。 選擇性。 同進程 COM 類別所使用的執行緒模型。 如果此屬性為 null，則不會使用任何執行緒模型。 元件是在用戶端的主執行緒上建立，而來自其他執行緒的呼叫會封送處理至此執行緒。 下列清單顯示有效的值：<br /><br /> `Apartment`、`Free`、`Both` 和 `Neutral`。|

## <a name="windowclass"></a>windowClass
 專案 `windowClass` 是專案的選擇性子系 `file` ，但如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式包含要使用免註冊的 com 來部署的 COM 元件，則可能需要此元素。 專案會參考 COM 元件所定義的視窗類別，該類別必須套用版本。 元素包含下列屬性。

|屬性|描述|
|---------------|-----------------|
|`versioned`|選擇性。 控制註冊中使用的內部視窗類別名稱是否包含含有視窗類別的元件版本。 這個屬性的值可以是 `yes` 或 `no` 。 預設為 `yes`。 `no`只有當並存元件和相等的非並存元件定義相同的視窗類別，且您想要將它們視為相同的視窗類別時，才應該使用此值。 請注意，有關視窗類別註冊的一般規則是適用的，只有註冊 window 類別的第一個元件才能夠註冊它，因為它沒有套用的版本。|

## <a name="hash"></a>雜湊
 `hash`元素是元素的選擇性子專案 `file` 。 `hash` 項目沒有任何屬性。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用應用程式中所有檔案的演算法雜湊做為安全性檢查，以確保在部署後不會變更任何檔案。 如果 `hash` 未包含此元素，則不會執行這項檢查。 因此， `hash` 不建議省略元素。

 如果資訊清單包含未雜湊的檔案，則該資訊清單無法進行數位簽署，因為使用者無法驗證未雜湊檔案的內容。

## <a name="dsigtransforms"></a>dsig:Transforms
 專案 `dsig:Transforms` 是專案的必要子項目 `hash` 。 `dsig:Transforms` 項目沒有任何屬性。

## <a name="dsigtransform"></a>dsig:Transform
 專案 `dsig:Transform` 是專案的必要子項目 `dsig:Transforms` 。 `dsig:Transform` 項目具有下列屬性。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前唯一使用的值 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為 `urn:schemas-microsoft-com:HashTransforms.Identity` 。 |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 專案 `dsig:DigestMethod` 是專案的必要子項目 `hash` 。 `dsig:DigestMethod` 項目具有下列屬性。

| 屬性 | 描述 |
|-------------| - |
| `Algorithm` | 用來計算此檔案摘要的演算法。 目前唯一使用的值 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為 `http://www.w3.org/2000/09/xmldsig#sha1` 。 |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 專案 `dsig:DigestValue` 是專案的必要子項目 `hash` 。 `dsig:DigestValue` 項目沒有任何屬性。 它的文字值是指定之檔案的計算雜湊。

## <a name="remarks"></a>備註
 這個元素會識別構成應用程式的所有 nonassembly 檔案，特別是檔案驗證的雜湊值。 這個元素也可以包含元件物件模型 (COM) 與檔案相關聯的隔離資料。 如果檔案變更，也必須更新應用程式資訊清單檔，以反映變更。

## <a name="example"></a>範例
 下列程式碼範例說明 `file` 使用部署之應用程式的應用程式資訊清單中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

```xml
<file name="Icon.ico" size="9216">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>
  </hash>
</file>
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)