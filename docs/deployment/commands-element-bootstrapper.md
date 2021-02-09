---
title: '&lt;啟動載入器) 的命令 &gt; 元素 (|Microsoft Docs'
description: 命令專案會在 InstallChecks 底下的元素中執行測試，並在 ClickOnce 啟動載入器測試失敗時宣告要安裝的封裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f53ca683e40be8e3cc428d013d2b8d3c8c5773e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881226"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;命令 &gt; 元素 (啟動載入器) 
專案會執行專案下的專案 `Commands` 所描述的測試 `InstallChecks` ，並宣告 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 當測試失敗時，啟動載入器應該安裝的封裝。

## <a name="syntax"></a>Syntax

```xml
<Commands
    Reboot
>
    <Command
        PackageFile
        Arguments
        EstimatedInstallSeconds
        EstimatedDiskBytes
        EstimatedTempBytes
        Log
    >
        <InstallConditions>
            <BypassIf
                Property
                Compare
                Value
                Schedule
            />
            <FailIf
                Property
                Compare
                Value
                String
                Schedule
            />
        </InstallConditions>
        <ExitCodes>
            <ExitCode
                Value
                Result
                String
            />
        </ExitCodes>
    </Command>
</Commands>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `Commands`需要元素。 元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Reboot`|選擇性。 判斷如果有任何套件傳回重新開機結束代碼，系統是否應該重新開機。 下列清單顯示有效的值：<br /><br /> `Defer`. 重新開機會延後到未來的某個時間。<br /><br /> `Immediate`. 如果其中一個套件傳回重新開機結束代碼，則會立即重新開機。<br /><br /> `None`. 會忽略任何重新開機要求。<br /><br /> 預設為 `Immediate`。|

## <a name="command"></a>命令
 `Command` 項目是 `Commands` 項目的子項目。 專案 `Commands` 可以有一或多個 `Command` 元素。 元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`PackageFile`|必要。 要安裝的封裝名稱應傳回 false 所指定的一或多個條件 `InstallConditions` 。 封裝必須在相同的檔案中使用元素來定義 `PackageFile` 。|
|`Arguments`|選擇性。 要傳遞至封裝檔案的一組命令列引數。|
|`EstimatedInstallSeconds`|選擇性。 安裝套件所需要的預估時間（以秒為單位）。 此值會決定啟動載入器顯示給使用者的進度列大小。 預設值為0，在此情況下不會指定任何時間估計。|
|`EstimatedDiskBytes`|選擇性。 安裝完成之後，套件將佔用的預估磁碟空間量（以位元組為單位）。 在啟動載入器向使用者顯示的硬碟空間需求中，會使用這個值。 預設值為0，在這種情況下，啟動載入器不會顯示任何硬碟空間需求。|
|`EstimatedTempBytes`|選擇性。 封裝將需要的暫存磁碟空間估計量（以位元組為單位）。|
|`Log`|選擇性。 封裝所產生之記錄檔的路徑（相對於封裝的根目錄）。|

## <a name="installconditions"></a>InstallConditions
 `InstallConditions`元素是元素的子系 `Command` 。 每個專案 `Command` 最多隻能有一個 `InstallConditions` 元素。 如果不 `InstallConditions` 存在任何專案，則 `Condition` 會一律執行指定的封裝。

## <a name="bypassif"></a>BypassIf
 專案 `BypassIf` 是專案的子系 `InstallConditions` ，並且描述不應執行命令的正則條件。 每個 `InstallConditions` 元素可以有零或多個 `BypassIf` 元素。

 `BypassIf` 具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要測試之屬性的名稱。 屬性之前必須由元素的子系定義 `InstallChecks` 。 如需詳細資訊，請參閱[ \<InstallChecks> 元素](../deployment/installchecks-element-bootstrapper.md)。|
|`Compare`|必要。 要執行的比較類型。 下列清單顯示有效的值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|必要。 要與屬性比較的值。|
|`Schedule`|選擇性。 `Schedule`定義何時應該評估此規則的標記名稱。|

## <a name="failif"></a>FailIf
 專案 `FailIf` 是專案的子系 `InstallConditions` ，並描述應該在其下停止安裝的正則條件。 每個 `InstallConditions` 元素可以有零或多個 `FailIf` 元素。

 `FailIf` 具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Property`|必要。 要測試之屬性的名稱。 屬性之前必須由元素的子系定義 `InstallChecks` 。 如需詳細資訊，請參閱[ \<InstallChecks> 元素](../deployment/installchecks-element-bootstrapper.md)。|
|`Compare`|必要。 要執行的比較類型。 下列清單顯示有效的值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|必要。 要與屬性比較的值。|
|`String`|選擇性。 失敗時對使用者顯示的文字。|
|`Schedule`|選擇性。 `Schedule`定義何時應該評估此規則的標記名稱。|

## <a name="exitcodes"></a>ExitCodes
 `ExitCodes`元素是元素的子系 `Command` 。 `ExitCodes`元素包含一或多個 `ExitCode` 元素，以決定要在回應封裝中的結束代碼時，所做的安裝動作。 元素底下可以有一個選擇性 `ExitCode` 元素 `Command` 。 `ExitCodes` 沒有任何屬性。

## <a name="exitcode"></a>ExitCode
 `ExitCode`元素是元素的子系 `ExitCodes` 。 `ExitCode`元素會決定安裝要做什麼，以回應封裝的結束代碼。 `ExitCode` 不包含任何子項目，而且具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Value`|必要。 套用此元素的結束代碼值 `ExitCode` 。|
|`Result`|必要。 安裝應該如何回應此結束代碼。 下列清單顯示有效的值：<br /><br /> `Success`. 將套件標記為已成功安裝。<br /><br /> `SuccessReboot`. 將套件標記為已安裝成功，並指示系統重新開機。<br /><br /> `Fail`. 將套件標記為失敗。<br /><br /> `FailReboot`. 將套件標記為失敗，並指示系統重新開機。|
|`String`|選擇性。 要對使用者顯示的值，以回應此結束代碼。|
|`FormatMessageFromSystem`|選擇性。 決定是否要使用系統提供的錯誤訊息，以對應到結束代碼，或使用中提供的值 `String` 。 有效的值是 `true` ，這表示使用系統提供的錯誤，以及 `false` 表示使用提供的字串 `String` 。 預設為 `false`。 如果這個屬性為 `false` ，但未 `String` 設定，則會使用系統提供的錯誤。|

## <a name="example"></a>範例
 下列程式碼範例會定義用於安裝 .NET Framework 2.0 的命令。

```xml
<Commands Reboot="Immediate">
    <Command PackageFile="instmsia.exe"
             Arguments= ' /q /c:"msiinst /delayrebootq"'
             EstimatedInstallSeconds="20" >
        <InstallConditions>
           <BypassIf Property="VersionNT" Compare="ValueExists"/>
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>
        </InstallConditions>
        <ExitCodes>
            <ExitCode Value="0" Result="SuccessReboot"/>
            <ExitCode Value="1641" Result="SuccessReboot"/>
            <ExitCode Value="3010" Result="SuccessReboot"/>
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
        </ExitCodes>
    </Command>
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"
             Arguments= '/quiet /norestart'
             EstimatedInstallSeconds="20" >
      <InstallConditions>
          <BypassIf Property="Version9x" Compare="ValueExists"/>
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>
      </InstallConditions>
      <ExitCodes>
          <ExitCode Value="0" Result="Success"/>
          <ExitCode Value="1641" Result="SuccessReboot"/>
          <ExitCode Value="3010" Result="SuccessReboot"/>
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
      </ExitCodes>
    </Command>
    <Command PackageFile="dotnetfx.exe"
         Arguments=' /q:a /c:"install /q /l"'
         EstimatedInstalledBytes="21000000"
         EstimatedInstallSeconds="300">

        <!-- These checks determine whether the package is to be installed -->
        <InstallConditions>
            <!-- Either of these properties indicates the .NET Framework is already installed -->
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>

            <!-- Block install if user does not have adminpermissions -->
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>

            <!-- Block install on Windows 95 -->
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>

            <!-- Block install on Windows 2000 SP 2 or less -->
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>

            <!-- Block install if Internet Explorer 5.01 or later is not present -->
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />

            <!-- Block install if the operating system does not support x86 -->
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />
       </InstallConditions>

        <ExitCodes>
            <ExitCode Value="0" Result="Success"/>
            <ExitCode Value="3010" Result="SuccessReboot"/>
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
        </ExitCodes>

    </Command>
</Commands>
```

## <a name="see-also"></a>另請參閱
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)
- [\<InstallChecks> 元素](../deployment/installchecks-element-bootstrapper.md)