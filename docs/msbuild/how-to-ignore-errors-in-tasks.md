---
title: 如何：忽略工作中的錯誤 | Microsoft Docs
description: 瞭解如何忽略 MSBuild 工作中的錯誤，以及控制組建在發生工作失敗時是否停止或繼續。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: f2c0b070868b8dc9fc10c4f493fbb75948485a5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914243"
---
# <a name="how-to-ignore-errors-in-tasks"></a>如何：忽略工作中的錯誤

有時您會希望組建能夠容忍某些工作中的錯誤。 如果這些非關鍵性的工作失敗，您會想要讓組建繼續執行，因為它仍然可以產生所需的輸出。 例如，如果專案使用 `SendMail` 工作，在建置每個元件之後傳送電子郵件訊息，您可能會考慮，即使郵件伺服器無法使用且無法傳送狀態訊息，還是能夠接受組建繼續完成。 或者，例如，如果通常會在建置期間刪除中繼資料檔案，您可能會考慮，即使無法刪除這些檔案，還是能夠接受組建繼續完成。

## <a name="use-the-continueonerror-attribute"></a>使用 ContinueOnError 屬性

`Task` 項目的 `ContinueOnError` 屬性可控制當工作失敗發生時，建置是否要停止或繼續。 此屬性也可控制當組建繼續時，是否要將錯誤視為錯誤或警告。

`ContinueOnError` 屬性可包含一或多個下列值：

- **WarnAndContinue** 或 **true**。 當工作失敗時， [目標](../msbuild/target-element-msbuild.md) 專案和組建中的後續工作會繼續執行，並將工作中的所有錯誤視為警告。

- **ErrorAndContinue**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。

- **ErrorAndStop** 或 **false** (預設值)。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。

只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。

`ContinueOnError` 的預設值為 `ErrorAndStop`。 如果將屬性設為 `ErrorAndStop`，就會明確地針對任何讀取專案檔的人做出此行為。

#### <a name="to-ignore-an-error-in-a-task"></a>忽略工作中的錯誤

使用工作的 `ContinueOnError` 屬性。 例如：

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>範例

下列程式碼範例將說明 `Build` 目標仍會執行，並將組建視為成功，即使 `Delete` 工作失敗也一樣。

```xml
<Project DefaultTargets="FakeBuild"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Files Include="*.obj"/>
    </ItemGroup>
    <Target Name="Clean">
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
    </Target>

    <Target Name="FakeBuild" DependsOnTargets="Clean">
        <Message Text="Building after cleaning..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
