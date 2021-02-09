---
title: GenerateApplicationManifest 工作 | Microsoft Docs
description: 使用 MSBuild GenerateApplicationManifest 工作來產生 ClickOnce 應用程式資訊清單或原生資訊清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2af490f27ab1cdecfe57da9253aff6c4247c7223
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914887"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest 工作

產生 ClickOnce 應用程式資訊清單或原生資訊清單。 原生資訊清單在描述元件時，會定義元件的唯一身分識別，並識別組成元件的所有組件和檔案。 ClickOnce 應用程式資訊清單會藉由指示應用程式的進入點，並指定應用程式安全性層級，來擴充原生資訊清單。

## <a name="parameters"></a>參數

下表說明 `GenerateApplicationManifest` 工作的參數。

| 參數 | Description |
|---------------------------------| - |
| `AssemblyName` | 選擇性的 `String` 參數。<br /><br /> 針對產生的資訊清單指定組件識別的 `Name` 欄位。 如果未指定此參數，會從 `EntryPoint` 或 `InputManifest` 參數來推斷名稱。 如果無法建立名稱，工作便會擲回錯誤。 |
| `AssemblyVersion` | 選擇性的 `String` 參數。<br /><br /> 針對產生的資訊清單指定組件識別的 `Version` 欄位。 如果未指定此參數，就會使用 "1.0.0.0" 的預設值。 |
| `ClrVersion` | 選擇性的 `String` 參數。<br /><br /> 指定應用程式所需的最小 Common Language Runtime (CLR) 版本。 預設值是建置系統所使用的 CLR 版本。 如果工作是要產生原生資訊清單，則會忽略此參數。 |
| `ConfigFile` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定包含應用程式組態檔的項目。 如果工作是要產生原生資訊清單，則會忽略此參數。 |
| `Dependencies` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定項目清單，這份清單會為所產生的資訊清單定義一組相依組件。 每個項目都可以利用項目中繼資料進一步描述，以指出其他部署狀態和相依性的類型。 如需詳細資訊，請參閱[項目中繼資料](#item-metadata)。 |
| `Description` | 選擇性的 `String` 參數。<br /><br /> 指定應用程式或元件的描述。 |
| `EntryPoint` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定單一項目，以指出所產生資訊清單組件的進入點。<br /><br /> 如果是 ClickOnce 應用程式資訊清單，這個參數會指定在執行應用程式時啟動的元件。 |
| `ErrorReportUrl` | 選擇性的 <xref:System.String?displayProperty=fullName> 參數。<br /><br /> 指定在 ClickOnce 安裝錯誤報告期間顯示於對話方塊中的網頁 URL。 |
| `FileAssociations` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定與 ClickOnce 部署資訊清單建立關聯之一或多個檔案類型的清單。<br /><br /> 檔案關聯只有在 .NET Framework 3.5 或更新版本設為目標時才有效。 |
| `Files` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要包含在資訊清單中的檔案。 指定每個檔案的完整路徑。 |
| `HostInBrowser` | 選擇性的 <xref:System.Boolean> 參數。<br /><br /> 如果為 `true`，表示應用程式是裝載於瀏覽器中 (與 WPF 網頁瀏覽器應用程式相同)。 |
| `IconFile` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 表示應用程式圖示檔。 應用程式圖示會在產生的應用程式資訊清單中表示，並用於 [ **開始] 功能表** 和 [ **新增/移除程式** ] 對話方塊。 如果未指定這項輸入，便會使用預設圖示。 如果工作是要產生原生資訊清單，則會忽略此參數。 |
| `InputManifest` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指出要作為資訊清單產生器基底的輸入 XML 文件。 這可讓結構化資料 (例如應用程式安全性或自訂資訊清單定義) 能夠反映在輸出資訊清單中。 XML 文件中的根元素必須是 asmv1 命名空間中的組件節點。 |
| `IsolatedComReferences` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要在所產生資訊清單中隔離的 COM 元件。 這個參數支援可在「免註冊的 COM」部署中隔離 COM 元件的功能。 其運作方式是利用標準的 COM 註冊定義來自動產生資訊清單。 不過，必須在建置電腦上註冊 COM 元件，才能讓這項功能正常運作。 |
| `ManifestType` | 選擇性的 `String` 參數。<br /><br /> 指定要產生的資訊清單類型。 此參數的值如下：<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> 如果未指定此參數，工作會預設為 `ClickOnce`。 |
| `MaxTargetPath` | 選擇性的 `String` 參數。<br /><br /> 指定 ClickOnce 應用程式部署中允許的檔案路徑長度上限。 如果指定這個值，則會根據這項限制來檢查應用程式中的每個檔案路徑長度。 任何超過限制的項目都會引發建置警告。 如果這項輸入未指定或為零，則不會執行任何檢查。 如果工作是要產生原生資訊清單，則會忽略此參數。 |
| `OSVersion` | 選擇性的 `String` 參數。<br /><br /> 指定應用程式所需的最小必要作業系統 (OS) 版本。 例如，"5.1.2600.0" 的值表示作業系統是 Windows XP。 如果未指定此參數，便會使用表示 Windows 98 Second Edition 的值 "4.10.0.0"，也就是 .NET Framework 支援的最小 OS 版本。 如果工作是要產生原生資訊清單，則會忽略這項輸入。 |
| `OutputManifest` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定所產生的輸出資訊清單檔名稱。 如果未指定此參數，會從產生的資訊清單識別來推斷輸出檔的名稱。 |
| `Platform` | 選擇性的 `String` 參數。<br /><br /> 指定應用程式的目標平台。 此參數的值如下：<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> 如果未指定此參數，工作會預設為 `AnyCPU`。 |
| `Product` | 選擇性的 `String` 參數。<br /><br /> 指定應用程式的名稱。 如果未指定此參數，會從產生的資訊清單識別來推斷名稱。 此名稱可用來作為 [開始] 功能表上的捷徑名稱，而且是出現在 [新增或移除程式] 對話方塊中名稱的一部分。 |
| `Publisher` | 選擇性的 `String` 參數。<br /><br /> 指定應用程式的發行者。 如果未指定此參數，會從已註冊使用者或產生的資訊清單識別來推斷名稱。 此名稱可用來作為 [開始] 功能表上的資料夾名稱，而且是出現在 [新增或移除程式] 對話方塊中名稱的一部分。 |
| `RequiresMinimumFramework35SP1` | 選擇性的 `Boolean` 參數。<br /><br /> 如果為 true，則應用程式需要 .NET Framework 3.5 SP1 或更新版本。 |
| `TargetCulture` | 選擇性的 `String` 參數。<br /><br /> 識別應用程式的文化特性，並為產生的資訊清單指定組件身分識別的 `Language` 欄位。 如果未指定此參數，則會假設應用程式不因文化特性而異。 |
| `TargetFrameworkMoniker` | 選擇性的 `String` 參數。<br /><br /> 指定目標 Framework Moniker。 |
| `TargetFrameworkProfile` | 選擇性的 `String` 參數。<br /><br /> 指定目標 Framework 設定檔。 |
| `TargetFrameworkSubset` | 選擇性的 `String` 參數。<br /><br /> 指定要設為目標之 .NET Framework 子集的名稱。 |
| `TargetFrameworkVersion` | 選擇性的 `String` 參數。<br /><br /> 指定專案的目標 .NET Framework。 |
| `TrustInfoFile` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 表示指定應用程式安全性的 XML 文件。 XML 文件中的根項目必須是 asmv2 命名空間中的 trustInfo 節點。 如果工作是要產生原生資訊清單，則會忽略此參數。 |
| `UseApplicationTrust` | 選擇性的 `Boolean` 參數。<br /><br /> 如果為 true，則 `Product`、`Publisher` 和 `SupportUrl` 屬性都會寫入應用程式資訊清單。 |

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.GenerateManifestBase> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需工作類別的參數清單，請參閱[工作基底類別](../msbuild/task-base-class.md)。

如需如何使用 `GenerateDeploymentManifest` 工作的資訊，請參閱 [GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)。

相依性和檔案的輸入可以進一步以項目中繼資料裝飾，以指定每個項目的其他部署狀態。

## <a name="item-metadata"></a>項目中繼資料

|中繼資料名稱|Description|
|-------------------|-----------------|
|`DependencyType`|指出相依性是以應用程式或必要條件進行發行和安裝。 這項中繼資料可用於所有相依性，但不能用於檔案。 此中繼資料可用的值如下：<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install 是預設值。|
|`AssemblyType`|指出相依性為 Managed 或原生組件。 這項中繼資料可用於所有相依性，但不能用於檔案。 此中繼資料可用的值如下：<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` 是預設值，表示資訊清單產生器將會自動決定組件類型。|
|`Group`|表示視需要下載額外檔案的群組。 群組名稱是由應用程式定義，並且可以是任何字串。 預設的空字串表示檔案不是下載群組的一部分。 不在群組中的檔案都是初始應用程式下載的一部分。 群組中的檔案只會在應用程式使用 <xref:System.Deployment.Application> 明確要求時下載。<br /><br /> 這項中繼資料可用於 `IsDataFile` 為 `false` 的所有檔案，以及 `DependencyType` 為 `Install` 的所有相依性。|
|`TargetPath`|指定應該如何在產生的資訊清單中定義路徑。 這個屬性可用於所有檔案。 如果未指定此屬性，便會使用項目規格。 這個屬性可用於 `DependencyType` 值為 `Install` 的所有檔案和相依性。|
|`IsDataFile`|`Boolean` 中繼資料值，指出檔案是否為資料檔案。 資料檔案的特殊性在於會在應用程式更新之間移轉。 這項中繼資料只可用於檔案。 `False` 為預設值。|

## <a name="example-1"></a>範例 1

此範例會使用此工作 `GenerateApplicationManifest` 來產生 ClickOnce 應用程式資訊清單，以及使用 `GenerateDeploymentManifest` 單一元件產生應用程式的部署資訊清單。 然後使用 `SignFile` 工作為資訊清單簽章。

這說明最簡單的資訊清單產生案例，其中會針對單一程式產生 ClickOnce 資訊清單。 預設名稱和身分識別都是從資訊清單的組件推斷而來。

> [!NOTE]
> 在以下範例中，所有應用程式二進位檔都會預先建置，以便讓您專注於資訊清單產生的各個方面。 此範例會產生完整運作的 ClickOnce 部署。
>
> [!NOTE]
> 如需本範例中 `SignFile` 工作所使用之 `Thumbprint` 屬性的詳細資訊，請參閱 [SignFile 工作](../msbuild/signfile-task.md)。

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            EntryPoint="@(EntryPoint)">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            EntryPoint="@(ApplicationManifest)">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-2"></a>範例 2

這個範例會使用 `GenerateApplicationManifest` 和工作 `GenerateDeploymentManifest` ，為具有單一元件的應用程式產生 ClickOnce 應用程式和部署資訊清單，並指定資訊清單的名稱和身分識別。

除了明確指定資訊清單的名稱和身分識別之外，這個範例與前一個範例類似。 此外，這個範例已設定為線上應用程式，而非安裝的應用程式。

> [!NOTE]
> 在以下範例中，所有應用程式二進位檔都會預先建置，以便讓您專注於資訊清單產生的各個方面。 此範例會產生完整運作的 ClickOnce 部署。
>
> [!NOTE]
> 如需本範例中 `SignFile` 工作所使用之 `Thumbprint` 屬性的詳細資訊，請參閱 [SignFile 工作](../msbuild/signfile-task.md)。

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            EntryPoint="@(EntryPoint)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
                AssemblyName="SimpleWinApp.application"
                AssemblyVersion="1.0.0.0"
                EntryPoint="@(ApplicationManifest)"
                Install="false"
                OutputManifest="SimpleWinApp.application">
                <Output
                    ItemName="DeployManifest"
                    TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-3"></a>範例 3

這個範例會使用 `GenerateApplicationManifest` 和工作， `GenerateDeploymentManifest` 為具有多個檔案和元件的應用程式產生 ClickOnce 應用程式和部署資訊清單。

> [!NOTE]
> 在以下範例中，所有應用程式二進位檔都會預先建置，以便讓您專注於資訊清單產生的各個方面。 此範例會產生完整運作的 ClickOnce 部署。
>
> [!NOTE]
> 如需本範例中 `SignFile` 工作所使用之 `Thumbprint` 屬性的詳細資訊，請參閱 [SignFile 工作](../msbuild/signfile-task.md)。

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
        <DeployUrl>
            <!-- Insert the deployment URL here -->
        </DeployUrl>
        <SupportUrl>
            <!-- Insert the support URL here -->
        </SupportUrl>
    </PropertyGroup>

    <Target Name="Build">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe"/>
        <Dependency Include="ClassLibrary1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <Dependency Include="ClassLibrary2.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <Group>Secondary</Group>
        </Dependency>
        <Dependency Include="MyAddIn1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>
        </Dependency>
        <Dependency Include="ClassLibrary3.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Prerequisite</DependencyType>
        </Dependency>

        <File Include="Text1.txt">
            <TargetPath>Text\Text1.txt</TargetPath>
            <Group>Text</Group>
        </File>
        <File Include="DataFile1.xml ">
            <TargetPath>Data\DataFile1.xml</TargetPath>
            <IsDataFile>true</IsDataFile>
        </File>

        <IconFile Include="Heart.ico"/>
        <ConfigFile Include="app.config">
            <TargetPath>SimpleWinApp.exe.config</TargetPath>
        </ConfigFile>
        <BaseManifest Include="app.manifest"/>
    </ItemGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            ConfigFile="@(ConfigFile)"
            Dependencies="@(Dependency)"
            Description="TestApp"
            EntryPoint="@(EntryPoint)"
            Files="@(File)"
            IconFile="@(IconFile)"
            InputManifest="@(BaseManifest)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            AssemblyName="SimpleWinApp.application"
            AssemblyVersion="1.0.0.0"
            DeploymentUrl="$(DeployToUrl)"
            Description="TestDeploy"
            EntryPoint="@(ApplicationManifest)"
            Install="true"
            OutputManifest="SimpleWinApp.application"
            Product="SimpleWinApp"
            Publisher="Microsoft"
            SupportUrl="$(SupportUrl)"
            UpdateEnabled="true"
            UpdateInterval="3"
            UpdateMode="Background"
            UpdateUnit="weeks">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-4"></a>範例 4

此範例使用 `GenerateApplicationManifest` 工作來產生應用程式 Test.exe 的原生資訊清單，並參考原生元件 Alpha.dll 和隔離的 COM 元件 Bravo.dll。

此範例會產生 Test.exe.manifest，讓應用程式 XCOPY 可部署並利用「免註冊的 COM」。

> [!NOTE]
> 在以下範例中，所有應用程式二進位檔都會預先建置，以便讓您專注於資訊清單產生的各個方面。 此範例會產生完整運作的 ClickOnce 部署。

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <File Include="Test.exe" />
        <Dependency Include="Alpha.dll">
            <AssemblyType>Native</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <ComComponent Include="Bravo.dll" />
    </ItemGroup>

    <Target Name="Build">
        <GenerateApplicationManifest
            AssemblyName="Test.exe"
            AssemblyVersion="1.0.0.0"
            Dependencies="@(Dependency)"
            Files="@(File)"
            IsolatedComReferences="@(ComComponent)"
            ManifestType="Native">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile 工作](../msbuild/signfile-task.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
