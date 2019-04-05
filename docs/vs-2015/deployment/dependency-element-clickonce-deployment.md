---
title: '&lt;相依性&gt;項目 （ClickOnce 部署） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941920"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;相依性&gt;項目 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

識別要安裝，應用程式的版本和應用程式資訊清單的位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `dependency`是必要元素。 它沒有任何屬性。 部署資訊清單可以有多個`dependency`項目。  
  
 `dependency`項目通常表示主應用程式的相依性組件內含[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式。 如果 Main.exe 應用程式會使用稱為 DotNetAssembly.dll 的組件，該組件必須在相依性一節中所列。 相依性，不過，也可以表示其他類型的相依性，例如倚賴特定版本的 common language runtime 中，在全域組件快取 (GAC) 中的組件或 COM 物件上。 因為它是一種自動部署技術，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]無法起始下載和安裝這些類型的相依性，但它不會防止應用程式執行如果一或多個指定的相依性不存在。  
  
## <a name="dependentassembly"></a>dependentAssembly  
 必要項。 這個項目包含`assemblyIdentity`項目。 下表顯示的屬性`dependentAssembly`支援。  
  
|屬性|描述|  
|---------------|-----------------|  
|`preRequisite`|選擇性。 指定這個組件應該已經存在於 GAC。 有效值為 `true` 和 `false`。 如果`true`，和指定的組件不存在於 GAC、 應用程式無法執行。|  
|`visible`|選擇性。 識別最上層應用程式身分識別，包括其相依性。 在內部使用[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]來管理應用程式存放區和啟用。|  
|`dependencyType`|必要項。 此相依性和應用程式之間的關係。 有效值為：<br /><br /> -   `install`. 元件代表目前的應用程式是個別安裝。<br />-   `preRequisite`. 目前的應用程式需要的元件。|  
|`codebase`|選擇性。 應用程式資訊清單的完整路徑。|  
|`size`|選擇性。 應用程式資訊清單，以位元組為單位的大小。|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 必要項。 這個元素是 `dependentAssembly` 元素的子項。 內容`assemblyIdentity`必須如所述相同[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式資訊清單。 下表顯示的屬性`assemblyIdentity`項目。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要項。 識別應用程式的名稱。|  
|`Version`|必要項。 指定的版本號碼的應用程式，以下列格式： `major.minor.build.revision`|  
|`publicKeyToken`|必要項。 指定 16 個字元的十六進位字串，表示簽署的應用程式或組件之公開金鑰的 sha-1 雜湊最後 8 個位元組。 用來登入的公用金鑰必須是 2048 位元或更高。|  
|`processorArchitecture`|必要項。 指定微處理器。 有效值`x86`用於 32 位元 Windows 和`IA64`的 64 位元 Windows。|  
|`Language`|選擇性。 識別組件的兩個組件語言代碼。 例如，EN-US，代表針對英文 （美國）。 預設為 `neutral`。 此元素為`asmv2`命名空間。|  
|`type`|選擇性。 針對回溯相容性 Windows-並存安裝技術。 唯一允許的值是`win32`。|  
  
## <a name="hash"></a>雜湊  
 `hash`項目是選用的子系`file`項目。 `hash` 項目沒有任何屬性。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 使用應用程式中的所有檔案的演算法雜湊做為安全性檢查，以確保沒有任何檔案已在部署後變更。 如果`hash`就不會包含項目，將不會執行這項檢查。 因此，省略`hash`不建議項目。  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`項目是必要的子系`hash`項目。 `dsig:Transforms` 項目沒有任何屬性。  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`項目是必要的子系`dsig:Transforms`項目。 下表顯示的屬性`dsig:Transform`項目。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Algorithm`|用來計算此檔案的摘要演算法。 目前所使用的唯一值[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]是`urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`項目是必要的子系`hash`項目。 下表顯示的屬性`dsig:DigestMethod`項目。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Algorithm`|用來計算此檔案的摘要演算法。 目前所使用的唯一值[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]是`http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 `dsig:DigestValue`項目是必要的子系`hash`項目。 `dsig:DigestValue` 項目沒有任何屬性。 它的值是計算的雜湊指定的檔案。  
  
## <a name="remarks"></a>備註  
 部署資訊清單通常會有單一`assemblyIdentity`可識別的名稱和版本的應用程式資訊清單的項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例所示`dependency`中的項目[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署資訊清單。  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定已安裝在 GAC 中的組件相依性。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定特定版本的通用語言執行平台上的相依性。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定作業系統相依性。  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> 元素](../deployment/dependency-element-clickonce-application.md)
