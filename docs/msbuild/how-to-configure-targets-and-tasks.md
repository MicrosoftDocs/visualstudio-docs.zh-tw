---
title: 如何：設定目標和工作 | Microsoft Docs
description: 瞭解如何設定選取的 MSBuild 工作，以在其目標環境中執行，而不論開發電腦的環境為何。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22dcb7a209b8a62aaeb3c036b1013e7ad3d21597
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914447"
---
# <a name="how-to-configure-targets-and-tasks"></a>如何：設定目標和工作

不論開發電腦的環境是哪一種，您都可以將選取的 MSBuild 工作設定為在所針對的環境中執行。 例如，當您使用 64 位元電腦來建置以 32 位元架構為目標的應用程式時，就會在 32 位元處理程序中執行選取的工作。
不論開發電腦的環境是哪一種，您都可以將選取的 MSBuild 工作設定為在所針對的環境中執行。 例如，當您使用 64 位元電腦來建置以 32 位元架構為目標的應用程式時，就會在 32 位元處理程序中執行選取的工作。

> [!NOTE]
> 如果是以 .NET 語言 (例如 Visual C# 或 Visual Basic) 來撰寫組建工作，而未使用原生資源或工具，則它不需任何修改，即可在任何目標內容中執行。

## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask 屬性和工作參數

下列 `UsingTask` 屬性會影響特定建置程序中工作的所有作業：

- `Runtime` 屬性如果存在的話，會設定通用語言執行平台 (CLR) 版本，並且可接受下列任何一個值：`CLR2`、`CLR4`、`CurrentRuntime` 或 `*` (任何執行階段)。

- `Architecture` 屬性如果存在的話，會設定平台和位元，並且可接受下列任何一個值：`x86`、`x64`、`CurrentArchitecture` 或 `*` (任何架構)。

- `TaskFactory` 屬性如果存在的話，會設定建立及執行工作執行個體的工作 Factory，並且只接受 `TaskHostFactory` 值。 如需詳細資訊，請參閱本文件中稍後的[工作 Factory](#task-factories)。

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

您也可以使用 `MSBuildRuntime` 和 `MSBuildArchitecture` 參數來設定個別工作的目標內容。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

在 MSBuild 執行工作之前，它會尋找具有相同目標內容的相符 `UsingTask`。 在 `UsingTask` 中指定但未在對應的工作中指定的參數會視為相符。 在工作中指定但未在對應的 `UsingTask` 中指定的參數也會視為相符。 如果未在 `UsingTask` 或工作中指定參數值，值就會預設為 `*` (任何參數)。

> [!WARNING]
> 如果有多個 `UsingTask` 存在且全部都有相符的 `TaskName`、`Runtime` 及 `Architecture` 屬性，則最後一個要評估的項目會取代其他項目。

 如果在工作上設定了參數，MSBuild 就會嘗試尋找與這些參數相符或至少不與它們衝突的 `UsingTask`。 可以有多個 `UsingTask` 來指定相同工作的目標內容。 例如，針對不同目標環境具有不同可執行檔的工作可能會像這樣：

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>工作 Factory

MSBuild 會在執行工作之前，先檢查看看它是否是指定為在目前的軟體內容中執行。 如果是這樣指定工作的，MSBuild 就會將它傳遞給 AssemblyTaskFactory 以在目前的處理程序中執行它；否則，MSBuild 會將工作傳遞給 TaskHostFactory 以在符合目標內容的處理程序中執行它。 即使目前的內容和目標內容相符，您仍可藉由將 `TaskFactory` 設定為 `TaskHostFactory`，來強制讓工作跨處理序執行 (基於隔離、安全性或其他原因)。

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>虛設項目工作參數

`MSBuildRuntime` 和 `MSBuildArchitecture` 與任何其他工作參數相同，都可從建置屬性來設定。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

不同於其他工作參數，`MSBuildRuntime` 和 `MSBuildArchitecture` 對於工作本身並不明顯。 若要撰寫知道執行所在內容的工作，您必須藉由呼叫 .NET Framework 來測試內容，或使用建置屬性以透過其他工作參數傳遞內容資訊。

> [!NOTE]
> `UsingTask` 屬性可以從工具組和環境屬性設定。

`MSBuildRuntime` 和 `MSBuildArchitecture` 參數提供最具彈性的方式，來設定目標內容，但是範圍也最受限制。 一方面，因為它們是設定在工作執行個體本身，並且在即將執行工作之前才會評估，所以它們可以從評估時間和建置階段可用屬性的完整範圍衍生其值。 在另一方面，這些參數僅適用於特定目標中工作的特定執行個體。

> [!NOTE]
> 工作參數是在父節點的內容中評估，不是工作主機的內容。 執行階段或架構相依的環境變數 (例如「程式檔案」位置) 將評估為符合父節點的值。 不過，如果工作直接讀取相同的環境變數，它會正確地在工作主機的內容中進行評估。

## <a name="see-also"></a>另請參閱

- [設定目標和工作](../msbuild/configuring-targets-and-tasks.md)
- [UsingTask 項目](../msbuild/usingtask-element-msbuild.md)
