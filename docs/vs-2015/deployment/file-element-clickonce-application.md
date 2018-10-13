---
title: '&lt;檔案&gt;項目 （ClickOnce 應用程式） |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 16c301d55738519f3e097138f08b6b2c2fe2b4c7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270734"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;檔案&gt;項目 （ClickOnce 應用程式）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

識別所有的非組件檔案下載，並由應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `file` 項目是選擇性的。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要。 識別檔案的名稱。|  
|`size`|必要。 指定的大小，以位元組為單位的檔案。|  
|`group`|選擇性，如果`optional`屬性沒有指定或設為`false`; 需要`optional`是`true`。 這個檔案所屬的群組名稱。 名稱可以是任何開發人員所選擇的 Unicode 字串值，以及用於下載檔案使用隨<xref:System.Deployment.Application.ApplicationDeployment>類別。|  
|`optional`|選擇性。 指定這個檔案必須下載第一個應用程式時執行，或是否檔案應該位於只能在伺服器上等到應用程式則會依需求要求它。 如果`false`或未定義，會下載檔案時第一次執行或安裝應用程式。 如果`true`、`group`必須指定有效的應用程式資訊清單。 `optional` 不能為 true 如果`writeableType`指定了值`applicationData`。|  
|`writeableType`|選擇性。 指定這個檔案是一個資料檔案。 目前唯一有效的值是`applicationData`。|  
  
## <a name="typelib"></a>型別程式庫  
 `typelib`項目是選擇性檔案項目的子系。 元素會描述屬於 COM 元件的類型程式庫。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`tlbid`|必要。 指派給類型程式庫的 GUID。|  
|`version`|必要。 型別程式庫版本號碼。|  
|`helpdir`|必要。 包含元件的說明檔案的目錄。 可能是長度為零。|  
|`resourceid`|選擇性。 地區設定識別碼 (LCID) 的十六進位字串表示法。 它是一到四個十六進位數字，不含 0x 前置詞，也沒有前置零。 LCID 可能有次要中性語言識別碼。|  
|`flags`|選擇性。 型別程式庫旗標，這個類型程式庫的字串表示。 具體來說，它應該是"RESTRICTED"、"CONTROL"、"HIDDEN"和"HASDISKIMAGE 」 的其中一個。|  
  
## <a name="comclass"></a>comClass  
 `comClass`項目是選用的子系`file`項目，但如果，則需要[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式包含想要使用免註冊 COM 部署的 COM 元件 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`clsid`|必要。 表示做為 GUID 的 COM 元件類別識別碼。|  
|`description`|選擇性。 類別名稱。|  
|`threadingModel`|選擇性。 同處理序 COM 類別所使用的執行緒模型。 如果此屬性為 null，則會使用沒有執行緒模型。 元件建立用戶端的主執行緒上，從其他執行緒的呼叫封送處理至這個執行緒。 下列清單顯示有效的值：<br /><br /> `Apartment`、 `Free`、 `Both`和 `Neutral`。|  
|`tlbid`|選擇性。 此 COM 元件的類型程式庫的 GUID。|  
|`progid`|選擇性。 與 COM 元件相關聯版本相依程式設計識別項。 格式`ProgID`是`<vendor>.<component>.<version>`。|  
|`miscStatus`|選擇性。 組件中的重複項目資訊清單所提供的資訊`MiscStatus`登錄機碼。 如果值`miscStatusIcon`， `miscStatusContent`， `miscStatusDocprint`，或`miscStatusThumbnail`找不到屬性，對應的預設值列在`miscStatus`用於遺漏的屬性。 值可以是下表中的屬性值的逗號分隔清單。 您可以使用這個屬性，如果 COM 類別是需要 OCX 類別`MiscStatus`登錄機碼值。|  
|`miscStatusIcon`|選擇性。 組件中的重複項目資訊清單 DVASPECT_ICON 所提供的資訊。 它可以提供物件的圖示。 值可以是下表中的屬性值的逗號分隔清單。 您可以使用這個屬性，如果 COM 類別是需要 OCX 類別`Miscstatus`登錄機碼值。|  
|`miscStatusContent`|選擇性。 組件中的重複項目資訊清單 DVASPECT_CONTENT 所提供的資訊。 它可以提供複合文件可顯示螢幕或印表機。 值可以是下表中的屬性值的逗號分隔清單。 您可以使用這個屬性，如果 COM 類別是需要 OCX 類別`MiscStatus`登錄機碼值。|  
|`miscStatusDocPrint`|選擇性。 組件中的重複項目資訊清單 DVASPECT_DOCPRINT 所提供的資訊。 它可以在螢幕上提供可顯示的物件表示，如同列印至印表機。 值可以是下表中的屬性值的逗號分隔清單。 您可以使用這個屬性，如果 COM 類別是需要 OCX 類別`MiscStatus`登錄機碼值。|  
|`miscStatusThumbnail`|選擇性。 組件中的重複項目資訊清單 DVASPECT_THUMBNAIL 所提供的資訊。 它可以提供以瀏覽工具可顯示物件的縮圖。 值可以是下表中的屬性值的逗號分隔清單。 您可以使用這個屬性，如果 COM 類別是需要 OCX 類別`MiscStatus`登錄機碼值。|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub`項目是選用的子系`file`項目，但如果可能需要[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式包含想要使用免註冊 COM 部署的 COM 元件 元素包含下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`iid`|必要。 介面識別碼 (IID) 這由這個 proxy。 IID 必須包含在括號括住它。|  
|`baseInterface`|選擇性。 從其介面則是所參考之介面的 IID`iid`衍生。|  
|`numMethods`|選擇性。 實作介面的方法數目。|  
|`name`|選擇性。 因為它的介面名稱會出現在程式碼。|  
|`tlbid`|選擇性。 包含描述所指定之介面的型別程式庫`iid`屬性。|  
|`proxyStubClass32`|選擇性。 將 IID 對應至在 32 位元 proxy Dll 的 CLSID。|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub`項目是選用的子系`file`項目，但如果可能需要[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式包含想要使用免註冊 COM 部署的 COM 元件 元素包含下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`iid`|必要。 介面識別碼 (IID) 這由這個 proxy。 IID 必須包含在括號括住它。|  
|`baseInterface`|選擇性。 從其介面則是所參考之介面的 IID`iid`衍生。|  
|`numMethods`|選擇性。 實作介面的方法數目。|  
|`Name`|選擇性。 因為它的介面名稱會出現在程式碼。|  
|`Tlbid`|選擇性。 包含描述所指定之介面的型別程式庫`iid`屬性。|  
|`proxyStubClass32`|選擇性。 將 IID 對應至在 32 位元 proxy Dll 的 CLSID。|  
|`threadingModel`|選擇性。 選擇性。 同處理序 COM 類別所使用的執行緒模型。 如果此屬性為 null，則會使用沒有執行緒模型。 元件建立用戶端的主執行緒上，從其他執行緒的呼叫封送處理至這個執行緒。 下列清單顯示有效的值：<br /><br /> `Apartment`、 `Free`、 `Both`和 `Neutral`。|  
  
## <a name="windowclass"></a>windowClass  
 `windowClass`項目是選用的子系`file`項目，但如果可能需要[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式包含想要使用免註冊 COM 部署的 COM 元件 此元素會參考 COM 元件，必須套用至該版本所定義的視窗類別。 元素包含下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`versioned`|選擇性。 控制項的內部視窗類別名稱註冊使用的是否包含含有視窗類別的組件的版本。 此屬性的值可以是`yes`或`no`。 預設為 `yes`。 值`no`只應在相同的視窗類別由並排顯示元件和定義對等的非---並存元件，而且您想將它們視為相同的視窗類別。 請注意，視窗類別註冊的一般規則適用 — 只有註冊視窗類別的第一個元件，才能夠註冊，因為它不能套用至它的版本。|  
  
## <a name="hash"></a>雜湊  
 `hash`項目是選用的子系`file`項目。 `hash` 項目沒有任何屬性。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 安全性檢查，以使用應用程式中的所有檔案的演算法雜湊，以確保沒有任何檔案已在部署後變更。 如果`hash`就不會包含項目，將不會執行這項檢查。 因此，省略`hash`不建議項目。  
  
 如果資訊清單包含不會進行雜湊的檔案，該資訊清單無法以數位方式簽署，因為使用者無法驗證雜湊檔案的內容。  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`項目是必要的子系`hash`項目。 `dsig:Transforms` 項目沒有任何屬性。  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`項目是必要的子系`dsig:Transforms`項目。 `dsig:Transform` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Algorithm`|用來計算此檔案的摘要演算法。 目前所使用的唯一值[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]是`urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`項目是必要的子系`hash`項目。 `dsig:DigestMethod` 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Algorithm`|用來計算此檔案的摘要演算法。 目前所使用的唯一值[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]是`http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 `dsig:DigestValue`項目是必要的子系`hash`項目。 `dsig:DigestValue` 項目沒有任何屬性。 它的值是計算的雜湊指定的檔案。  
  
## <a name="remarks"></a>備註  
 此項目可識別組成應用程式的所有非組件檔案，並特別的是，雜湊值的檔案驗證。 這個項目也可以包含檔案相關聯的元件物件模型 (COM) 隔離資料。 如果變更的檔案，應用程式資訊清單檔案也必須更新以反映變更。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`file`的部署使用的應用程式資訊清單的應用程式中的項目[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]。  
  
```  
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
 [ndptecclick](../deployment/clickonce-application-manifest.md)



