---
title: '&lt;啟動載入器 &gt;)  (InstallChecks 元素 |Microsoft Docs'
description: InstallChecks 元素支援在本機電腦上啟動各種測試，以確保已安裝應用程式的所有必要條件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 550baf52347c1128ef50509e7787861355c9428f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903399"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;啟動載入器 &gt;)  (InstallChecks 元素
`InstallChecks`元素支援針對本機電腦啟動各種測試，以確保已安裝應用程式的所有適當必要條件。

## <a name="syntax"></a>Syntax

```xml
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
 這個元素是的選擇性子項目 `InstallChecks` 。 針對的每個實例，啟動載入器將確保專案所 `AssemblyCheck` 識別的元件存在於全域組件快取 (GAC) 中。 它不包含任何元素，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要儲存結果的屬性名稱。 這個屬性可以從專案下的測試參考 `InstallConditions` ，也就是專案的子系 `Command` 。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。|
|`Name`|必要。 要檢查之元件的完整名稱。|
|`PublicKeyToken`|必要。 與此強式名稱元件相關聯之公開金鑰的縮寫形式。 儲存在 GAC 中的所有元件都必須具有名稱、版本和公開金鑰。|
|`Version`|必要。 組件的版本。<br /><br /> 版本號碼的格式 ...。 \<*major version*> \<*minor version*> \<*build version*> \<*revision version*>|
|`Language`|選擇性。 當地語系化元件的語言。 預設為 `neutral`。|
|`ProcessorArchitecture`|選擇性。 此安裝的目的電腦處理器。 預設為 `msil`。|

## <a name="externalcheck"></a>ExternalCheck
 這個元素是的選擇性子項目 `InstallChecks` 。 針對的每個實例，啟動載入器 `ExternalCheck` 會在個別的進程中執行命名的外部程式，並將它的結束代碼儲存在所指示的屬性中 `Property` 。 `ExternalCheck` 適用于執行複雜的相依性檢查，或檢查元件是否存在的唯一方法是將它具現化。

 `ExternalCheck` 未包含任何元素，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要儲存結果的屬性名稱。 這個屬性可以從專案下的測試參考 `InstallConditions` ，也就是專案的子系 `Command` 。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。|
|`PackageFile`|必要。 要執行的外部程式。 程式必須是安裝程式散發套件的一部分。|
|`Arguments`|選擇性。 提供命令列引數給所命名的可執行檔 `PackageFile` 。|

## <a name="filecheck"></a>FileCheck
 這個元素是的選擇性子項目 `InstallChecks` 。 針對的每個實例，啟動載入器 `FileCheck` 會判斷指定的檔案是否存在，並傳回檔案的版本號碼。 如果檔案沒有版本號碼，啟動載入器會將名為的屬性設定 `Property` 為0。 如果檔案不存在， `Property` 則不會設定為任何值。

 `FileCheck` 未包含任何元素，而且具有下列屬性。

| 屬性 | 描述 |
|-----------------| - |
| `Property` | 必要。 要儲存結果的屬性名稱。 這個屬性可以從專案下的測試參考 `InstallConditions` ，也就是專案的子系 `Command` 。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。 |
| `FileName` | 必要。 要尋找的檔案名。 |
| `SearchPath` | 必要。 要在其中尋找檔案的磁片或資料夾。 如果已指派，這必須是相對路徑 `SpecialFolder` ; 否則，它必須是絕對路徑。 |
| `SpecialFolder` | 選擇性。 對 Windows 或而言具有特殊意義的資料夾 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 預設值是解讀為 `SearchPath` 絕對路徑。 有效值如下：<br /><br /> `AppDataFolder`. 此應用程式的應用程式資料夾，專 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 屬於目前的使用者。<br /><br /> `CommonAppDataFolder`. 所有使用者所使用的應用程式資料檔案夾。<br /><br /> `CommonFilesFolder`. 目前使用者的 Common Files 資料夾。<br /><br /> `LocalDataAppFolder`. 非漫遊應用程式的 [資料] 資料夾。<br /><br /> `ProgramFilesFolder`. 32位應用程式的標準 [Program Files] 資料夾。<br /><br /> `StartUpFolder`. 此資料夾包含在系統啟動時啟動的所有應用程式。<br /><br /> `SystemFolder`. 包含32位系統 Dll 的資料夾。<br /><br /> `WindowsFolder`. 包含 Windows 系統安裝的資料夾。<br /><br /> `WindowsVolume`. 包含 Windows 系統安裝的磁片磁碟機或磁碟分割。 |
| `SearchDepth` | 選擇性。 要在其中搜尋指定檔案之子資料夾的深度。 搜尋是深度優先。 預設值為0，這會將搜尋限制為由和 SearchPath 指定的最上層資料夾 `SpecialFolder` 。  |

## <a name="msiproductcheck"></a>MsiProductCheck
 這個元素是的選擇性子項目 `InstallChecks` 。 針對的每個實例，啟動載入器 `MsiProductCheck` 會先檢查指定的 Microsoft Windows Installer 安裝是否已執行，直到完成為止。 屬性值會根據所安裝產品的狀態進行設定。 正值表示已安裝產品，0或-1 表示未安裝。  (如需詳細資訊，請參閱 Windows Installer SDK 函數 MsiQueryFeatureState。 ) 。 如果電腦上未安裝 Windows Installer， `Property` 則不會設定。

 `MsiProductCheck` 未包含任何元素，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要儲存結果的屬性名稱。 這個屬性可以從專案下的測試參考 `InstallConditions` ，也就是專案的子系 `Command` 。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。|
|`Product`|必要。 已安裝產品的 GUID。|
|`Feature`|選擇性。 已安裝應用程式之特定功能的 GUID。|

## <a name="registrycheck"></a>RegistryCheck
 這個元素是的選擇性子項目 `InstallChecks` 。 針對的每個實例，啟動載入器會 `RegistryCheck` 檢查指定的登錄機碼是否存在，或是否有指定的值。

 `RegistryCheck` 未包含任何元素，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要儲存結果的屬性名稱。 這個屬性可以從專案下的測試參考 `InstallConditions` ，也就是專案的子系 `Command` 。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。|
|`Key`|必要。 登錄機碼的名稱。|
|`Value`|選擇性。 要取出的登錄值名稱。 預設值是傳回預設值的文字。 `Value` 必須是字串或 DWORD。|

## <a name="registryfilecheck"></a>RegistryFileCheck
 這個元素是的選擇性子項目 `InstallChecks` 。 針對的每個實例，啟動載入器會 `RegistryFileCheck` 先嘗試從指定的登錄機碼取出檔案的路徑，以抓取指定檔案的版本。 如果您想要在指定為登錄中值的目錄中查詢檔案，這會特別有用。

 `RegistryFileCheck` 未包含任何元素，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要儲存結果的屬性名稱。 這個屬性可以從專案下的測試參考 `InstallConditions` ，也就是專案的子系 `Command` 。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。|
|`Key`|必要。 登錄機碼的名稱。 除非已設定屬性，否則它的值會被解釋為檔案的路徑 `File` 。 如果此機碼不存在， `Property` 則不會設定。|
|`Value`|選擇性。 要取出的登錄值名稱。 預設值是傳回預設值的文字。 `Value` 必須是字串。|
|`FileName`|選擇性。 檔案名。 如果指定，則會假設從登錄機碼取得的值是目錄路徑，並將此名稱附加至該路徑。 如果未指定，則會假設從登錄傳回的值為檔案的完整路徑。|
|`SearchDepth`|選擇性。 要在其中搜尋指定檔案之子資料夾的深度。 搜尋是深度優先。 預設值為0，這會將搜尋限制為登錄機碼值所指定的最上層資料夾。|

## <a name="remarks"></a>備註
 當下的元素 `InstallChecks` 定義要執行的測試時，不會執行這些測試。 若要執行測試，您必須在專案 `Command` 底下建立元素 `Commands` 。

## <a name="example"></a>範例
 下列程式碼範例將示範在 `InstallChecks` .NET Framework 的產品檔中使用的元素。

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 當 `InstallChecks` 評估時，它們會產生屬性。 然後，會使用屬性 `InstallConditions` 來判斷封裝是否應該安裝、略過或失敗。 下表列出 `InstallConditions` ：

|條件|描述|
|-|-|
|`FailIf`|如果任何 `FailIf` 條件評估為 true，則封裝會失敗。 其餘的條件將不會進行評估。|
|`BypassIf`|如果有任何 `BypassIf` 條件評估為 true，則會略過封裝。 其餘的條件將不會進行評估。|

## <a name="predefined-properties"></a>預先定義的屬性
 下表列出 `BypassIf` 和 `FailIf` 元素：

|屬性|備註|可能的值|
|--------------|-----------|---------------------|
|`Version9X`|Windows 9X 作業系統的版本號碼。|4.10 = Windows 98|
|`VersionNT`|以 Windows NT 為基礎之作業系統的版本號碼。|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|以64位 Windows NT 為基礎之作業系統的版本號碼。|如同稍早所述。|
|`VersionMsi`|Windows Installer 服務的版本號碼。|2.0 = Windows Installer 2。0|
|`AdminUser`|指定使用者是否擁有以 Windows NT 為基礎之作業系統的系統管理員許可權。|0 = 無系統管理員許可權<br /><br /> 1 = 系統管理員許可權|

 例如，若要在執行 Windows 95 的電腦上封鎖安裝，請使用如下所示的程式碼：

```xml
    <!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

 若要在符合 FailIf 或 BypassIf 條件時跳過執行安裝檢查，請使用 BeforeInstallChecks 屬性。  例如：

```xml
    <!-- Block install and do not evaluate install checks if user does not have admin privileges -->
    <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired" BeforeInstallChecks="true"/>
```

>[!NOTE]
>`BeforeInstallChecks`從 Visual Studio 2019 Update 9 版本開始支援此屬性。

## <a name="see-also"></a>另請參閱
- [\<Commands> 元素](../deployment/commands-element-bootstrapper.md)
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)