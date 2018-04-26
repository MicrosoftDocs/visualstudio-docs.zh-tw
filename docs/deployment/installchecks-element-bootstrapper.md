---
title: '&lt;InstallChecks&gt;元素 （啟動載入器） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcfd8aaa0048cac3fb9a33c7974132655de87a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt;元素 （啟動載入器）
`InstallChecks`項目支援啟動各種不同的測試以確定所有適當的應用程式的必要條件都已安裝在本機電腦。  
  
## <a name="syntax"></a>語法  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 這個項目是選擇性子項目`InstallChecks`。 每個執行個體`AssemblyCheck`，啟動載入器可確保在全域組件快取 (GAC) 中有項目所識別的組件。 包含任何項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 若要將結果儲存屬性的名稱。 這個屬性可參考下測試的`InstallConditions`項目子系的`Command`項目。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Name`|必要。 若要檢查組件的完整限定的名稱。|  
|`PublicKeyToken`|必要。 與這具備強式名稱組件相關聯的公開金鑰縮寫的格式。 儲存在 GAC 中的所有組件必須具有名稱、 版本，以及公開金鑰。|  
|`Version`|必要。 組件的版本。<br /><br /> 版本號碼的格式\<*主要版本*>。\<*次要版本*>。\<*組建版本*>。\<*修訂版本*>。|  
|`Language`|選擇性。 當地語系化的組件的語言。 預設為 `neutral`。|  
|`ProcessorArchitecture`|選擇性。 此安裝的目標電腦處理器。 預設為 `msil`。|  
  
## <a name="externalcheck"></a>ExternalCheck  
 這個項目是選擇性子項目`InstallChecks`。 每個執行個體`ExternalCheck`，啟動載入器會在個別的處理序中執行具名的外部程式，並將它的結束代碼儲存在所指示的屬性`Property`。 `ExternalCheck` 適用於實作複雜的相依性檢查，或檢查元件存在的唯一方式是將它執行個體化。  
  
 `ExternalCheck` 包含任何項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 若要將結果儲存屬性的名稱。 這個屬性可參考下測試的`InstallConditions`項目子系的`Command`項目。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
|`PackageFile`|必要。 要執行的外部程式。 該程式必須是安裝程式發佈封裝的一部分。|  
|`Arguments`|選擇性。 命令列引數提供給可執行檔名為`PackageFile`。|  
  
## <a name="filecheck"></a>FileCheck  
 這個項目是選擇性子項目`InstallChecks`。 每個執行個體`FileCheck`，啟動載入器會判斷檔案是否存在，以及傳回檔案的版本號碼。 啟動載入器檔案並沒有版本號碼，如果設定所命名的屬性`Property`設為 0。 如果檔案不存在，`Property`未設定任何值。  
  
 `FileCheck` 包含任何項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 若要將結果儲存屬性的名稱。 這個屬性可參考下測試的`InstallConditions`項目子系的`Command`項目。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
|`FileName`|必要。 要尋找檔案的名稱。|  
|`SearchPath`|必要。 磁碟或要在其中尋找檔案的資料夾中。 這必須是相對路徑，如果`SpecialFolder`指派; 否則它必須是絕對路徑。|  
|`SpecialFolder`|選擇性。 具有特殊意義，windows 或為資料夾[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 預設值是將解譯`SearchPath`做為絕對路徑。 有效值包括以下的值：<br /><br /> `AppDataFolder`. 這個應用程式資料資料夾[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的應用程式; 特定於目前的使用者。<br /><br /> `CommonAppDataFolder`. 所有使用者都使用的應用程式儲存資料夾。<br /><br /> `CommonFilesFolder`. 目前的使用者共用檔案資料夾。<br /><br /> `LocalDataAppFolder`. 非漫遊應用程式資料資料夾。<br /><br /> `ProgramFilesFolder`. 32 位元應用程式的標準 Program Files 資料夾。<br /><br /> `StartUpFolder`. 包含在系統啟動時啟動的所有應用程式的資料夾。<br /><br /> `SystemFolder`. 包含 32 位元系統 Dll 的資料夾。<br /><br /> `WindowsFolder`. Windows 系統安裝所在的資料夾。<br /><br /> `WindowsVolume`. 磁碟機或磁碟分割包含 Windows 系統安裝。|  
|`SearchDepth`|選擇性。 要針對具名檔案的子資料夾中搜尋深度。 搜尋是深度優先。 預設值為 0，將搜尋限制到所指定的最上層資料夾`SpecialFolder`和**SearchPath**。|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 這個項目是選擇性子項目`InstallChecks`。 每個執行個體`MsiProductCheck`，啟動載入器會檢查指定的 Microsoft Windows Installer 安裝是否已執行，直到完成為止。 屬性值設定視安裝之產品的狀態而定。 正值表示已安裝產品，0 或-1 表示未安裝。 （請參閱 Windows Installer SDK 函式 MsiQueryFeatureState，如需詳細資訊）. 如果在電腦上未安裝 Windows Installer`Property`未設定。  
  
 `MsiProductCheck` 包含任何項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 若要將結果儲存屬性的名稱。 這個屬性可參考下測試的`InstallConditions`項目子系的`Command`項目。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Product`|必要。 已安裝產品的 GUID。|  
|`Feature`|選擇性。 安裝的應用程式的特定功能的 GUID。|  
  
## <a name="registrycheck"></a>RegistryCheck  
 這個項目是選擇性子項目`InstallChecks`。 每個執行個體`RegistryCheck`，啟動載入器會檢查以查看指定的登錄機碼是否存在，或是否有指定的值。  
  
 `RegistryCheck` 包含任何項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 若要將結果儲存屬性的名稱。 這個屬性可參考下測試的`InstallConditions`項目子系的`Command`項目。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必要。 登錄機碼的名稱。|  
|`Value`|選擇性。 要擷取之登錄值名稱。 預設會傳回預設值的文字。 `Value` 必須是字串或 DWORD。|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 這個項目是選擇性子項目`InstallChecks`。 每個執行個體`RegistryFileCheck`，啟動載入器會擷取指定的檔案版本第一次嘗試從指定的登錄機碼擷取至檔案的路徑。 這是特別有用，如果您想要查閱登錄中的值為指定的目錄中的檔案。  
  
 `RegistryFileCheck` 包含任何項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 若要將結果儲存屬性的名稱。 這個屬性可參考下測試的`InstallConditions`項目子系的`Command`項目。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必要。 登錄機碼的名稱。 其值會解譯成檔案的路徑，除非`File`屬性設定。 如果此機碼不存在，`Property`未設定。|  
|`Value`|選擇性。 要擷取之登錄值名稱。 預設會傳回預設值的文字。 `Value` 必須是字串。|  
|`FileName`|選擇性。 檔案名稱。 如果指定，取得從登錄機碼的值會假設是一個目錄路徑，而此名稱會附加到其。 如果未指定，從登錄所傳回的值會假設檔案的完整路徑。|  
|`SearchDepth`|選擇性。 要針對具名檔案的子資料夾中搜尋深度。 搜尋是深度優先。 預設值為 0，將搜尋限制的登錄機碼值所指定的最上層資料夾。|  
  
## <a name="remarks"></a>備註  
 雖然下方的項目`InstallChecks`定義要執行的測試，它們不會執行它們。 若要執行測試，您必須建立`Command`下方的項目`Commands`項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範`InstallChecks`項目，因為它用於產品檔案[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 當`InstallChecks`會進行評估，產生的屬性。 然後會使用屬性`InstallConditions`來判斷封裝是否應該安裝、 略過，或失敗。 下表列出`InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|如果有任何`FailIf`條件評估為 true，封裝將會失敗。 這些條件的其餘部分將不評估。|  
|`BypassIf`|如果有任何`BypassIf`條件評估為 true，將會略過的封裝。 這些條件的其餘部分將不評估。|  
  
## <a name="predefined-properties"></a>預先定義的屬性  
 下表列出`BypassIf`和`FailIf`項目：  
  
|屬性|注意|可能的值|  
|--------------|-----------|---------------------|  
|`Version9X`|Windows 9x X 作業系統版本號碼。|4.10 = Windows 98|  
|`VersionNT`|Windows NT 系列作業系統的版本號碼。|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|64 位元 Windows NT 系列作業系統的版本號碼。|稍早所提的相同。|  
|`VersionMsi`|Windows Installer 服務的版本號碼。|2.0 = Windows Installer 2.0|  
|`AdminUser`|指定使用者是否在 Windows NT 系列作業系統上具有系統管理員權限。|0 = 沒有系統管理員權限<br /><br /> 1 = 系統管理員權限|  
  
 例如，若要封鎖執行 Windows 95 的電腦上安裝，使用程式碼如下所示：  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<命令 > 項目](../deployment/commands-element-bootstrapper.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)