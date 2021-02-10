---
title: '&lt;&gt;ClickOnce 應用程式)  (trustInfo 元素 |Microsoft Docs'
description: TrustInfo 元素會描述應用程式在用戶端電腦上執行所需的最低安全性許可權。 TrustInfo 元素是必要專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e91bdb2e842692224564374e3f9f4d23cf71cf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945015"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt; 元素 (ClickOnce 應用程式)
描述應用程式在用戶端電腦上執行所需的最低安全性權限。

## <a name="syntax"></a>Syntax

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `trustInfo` 項目是必要的，且位於 `asm.v2` 命名空間。 其沒有屬性，包含下列元素。

## <a name="security"></a>security
 必要。 這個元素是 `trustInfo` 元素的子項。 其包含 `applicationRequestMinimum` 元素，而沒有屬性。

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 必要。 這個元素是 `security` 元素的子項，並包含 `PermissionSet`、 `assemblyRequest`與 `defaultAssemblyRequest`元素。 這個元素沒有屬性。

## <a name="permissionset"></a>PermissionSet
 必要。 這個元素是 `applicationRequestMinimum` 元素的子項，並包含 `IPermission` 元素。 這個項目具有下列屬性。

- `ID`

     必要。 識別權限集合。 這個屬性可以是任何值。 識別碼在 `defaultAssemblyRequest` 和 `assemblyRequest` 屬性中受參考。

- `version`

     必要。 識別權限版本。 這個值通常是 `1`。

## <a name="ipermission"></a>IPermission
 選擇性。 這個元素是 `PermissionSet` 元素的子項。 `IPermission`元素會完整識別 .NET Framework 中的許可權類別。 `IPermission` 元素有下列屬性，但可以有對應到權限類別上屬性 (property) 的其他屬性 (attribute)。 若要取得特定權限的語法，請查看 Security.config 檔案所列範例。

- `class`

     必要。 依強式名稱識別權限類別。 例如，下列程式碼可識別 `FileDialogPermission` 類型。

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     必要。 識別權限版本。 這個值通常是 `1`。

- `Unrestricted`

     必要。 識別應用程式是否需要這個權限不受限制的授與。 如果為 `true`，即無條件權限授與。 如果為 `false`或未定義屬性，則根據 `IPermission` 標記上定義的權限特有屬性而受限。 採用下列權限：

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     在這個範例中， <xref:System.Security.Permissions.EnvironmentPermission> 的宣告會將應用程式限制為只能讀取環境變數 USERNAME，而 <xref:System.Security.Permissions.FileDialogPermission> 的宣告則讓應用程式不受限制地使用所有 <xref:System.Windows.Forms.FileDialog> 類別。

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 選擇性。 識別授與所有組件的權限集合。 這個元素是 `applicationRequestMinimum` 元素的子項，並具有下列屬性。

- `permissionSetReference`

     必要。 識別預設權限的權限集合識別碼。 權限集合在 `PermissionSet` 元素中宣告。

## <a name="assemblyrequest"></a>assemblyRequest
 選擇性。 識別特定組件的權限。 這個元素是 `applicationRequestMinimum` 元素的子項，並具有下列屬性。

- `Name`

     必要。 識別組件名稱。

- `permissionSetReference`

     必要。 識別這個組件需要的權限集合識別碼。 權限集合在 `PermissionSet` 元素中宣告。

## <a name="requestedprivileges"></a>requestedPrivileges
 選擇性。 這個元素是 `security` 元素的子項，並包含 `requestedExecutionLevel` 元素。 這個元素沒有屬性。

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 選擇性。 識別要執行應用程式要求的安全性層級。 這個元素沒有子項，並具有下列屬性。

- `Level`

   必要。 指出應用程式要求的安全性層級。 可能的值包括：

   `asInvoker`，未要求其他權限。 這個層級不需要其他信任提示。

   `highestAvailable`，要求父處理序可提供的最高權限。

   `requireAdministrator`，要求完整系統管理員權限。

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式只能以 `asInvoker`值安裝。 以其他任何值安裝則會失敗。

- `uiAccess`

   選擇性。 指出應用程式是否需要存取受保護的使用者介面元素。 值可以是 `true` 或 `false`，預設為 false。 只有已簽署的應用程式可使用值 true。

## <a name="remarks"></a>備註
 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式要求的權限比用戶端電腦預設要授與者更高，通用語言執行平台的信任管理員會詢問使用者是否要授與應用程式這個提高權限的信任層級。 如果使用者拒絕，應用程式就不會執行；否則會以要求的權限執行。

 如果部署資訊清單有有效的信任授權，所有使用 `defaultAssemblyRequest` 與 `assemblyRequest` 要求的權限就都會在不提示使用者的情況下授與。

 如需許可權提升的詳細資訊，請參閱 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。 如需原則部署的詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。

## <a name="examples"></a>範例
 下列三個程式碼範例說明了適用於 `trustInfo` 部署應用程式資訊清單中預設具名安全性區域 (Internet、LocalIntranet 及 FullTrust) 的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 元素。

 第一個範例說明 `trustInfo` 元素，適用於 Internet 安全性區域中提供的預設權限。

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 第二個範例說明 `trustInfo` 元素，適用於 LocalIntranet 安全性區域中提供的預設權限。

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 第三個範例說明 `trustInfo` 元素，適用於 FullTrust 安全性區域中提供的預設權限。

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>另請參閱
- [受信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)