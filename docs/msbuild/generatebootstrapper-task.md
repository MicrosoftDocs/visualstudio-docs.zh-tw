---
title: GenerateBootstrapper 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f18b01a6db0068b44ad9c25037e544efa8df35a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746591"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper 工作
提供自動化方式來偵測、下載及安裝應用程式及其必要條件。 它可用來做為單一安裝程式，針對組成應用程式的所有元件整合個別的安裝程式。

## <a name="task-parameters"></a>工作參數
以下描述 `GenerateBootstrapper` 工作的參數。

- `ApplicationFile`

   選擇性的 `String` 參數。

   指定啟動載入器將用來在安裝所有必要條件之後開始安裝應用程式的檔案。 如果未指定 `BootstrapperItems` 和 `ApplicationFile` 參數，將會產生建置錯誤。

- `ApplicationName`

   選擇性的 `String` 參數。

   指定啟動載入器將安裝的應用程式名稱。 此名稱將在安裝期間出現於啟動載入器所使用的 UI 中。

- `ApplicationRequiresElevation`

   選擇性的 `Boolean` 參數。

   如果是 `true`，則在目標電腦上安裝元件時，該元件會以更高的權限來執行。

- `ApplicationUrl`

   選擇性的 `String` 參數。

   指定裝載應用程式安裝程式的 Web 位置。

- `BootstrapperComponentFiles`

   選擇性的 `String[]` 輸出參數。

   指定啟動載入器封裝檔案的建置位置。

- `BootstrapperItems`

   選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。

   指定要在啟動載入器內建置的產品。 傳遞給此參數的項目應具有下列語法：

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   `Include` 屬性代表應該安裝的必要條件名稱。 `ProductName` 項目中繼資料為選擇性，而且萬一找不到套件，建置引擎將使用它作為易記名稱。 除非未指定 `ApplicationFile`，否則這些項目不是必要的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 輸入參數。 您應該基於每個必須針對您應用程式安裝的必要條件包含一個項目。

   如果未指定 `BootstrapperItems` 和 `ApplicationFile` 參數，將會產生建置錯誤。

- `BootstrapperKeyFile`

   選擇性的 `String` 輸出參數。

   指定 *setup.exe* 的建置位置

- `ComponentsLocation`

   選擇性的 `String` 參數。

   指定啟動載入器用來尋找要安裝之安裝必要條件的位置。 此參數的值如下：

  - `HomeSite`：表示必要條件已由元件廠商所裝載。

  - `Relative`：表示必要條件位於應用程式的相同位置。

  - `Absolute`：表示可在集中式 URL 中找到所有元件。 此值應該與 `ComponentsUrl` 輸入參數搭配使用。

    如果未指定 `ComponentsLocation`，預設會使用 `HomeSite`。

- `ComponentsUrl`

   選擇性的 `String` 參數。

   指定包含安裝必要條件的 URL。

- `CopyComponents`

   選擇性的 `Boolean` 參數。

   如果是 `true`，啟動載入器會將所有輸出檔案複製到 `OutputPath` 參數中指定的路徑。 `BootstrapperComponentFiles` 參數的值全部都應以此路徑為依據。 如果是 `false`，不會複製檔案，而 `BootstrapperComponentFiles` 值會以 `Path` 參數的值為依據。  此參數的預設值為 `true`。

- `Culture`

   選擇性的 `String` 參數。

   指定用於啟動載入器 UI 和安裝必要條件的文化特性。 無法使用指定的文化特性時，工作會使用 `FallbackCulture` 參數的值。

- `FallbackCulture`

   選擇性的 `String` 參數。

   指定用於啟動載入器 UI 和安裝必要條件的次要文化特性。

- `OutputPath`

   選擇性的 `String` 參數。

   指定要複製 *setup.exe* 和所有套件檔案的位置。

- `Path`

   選擇性的 `String` 參數。

   指定所有可用必要條件封裝的位置。

- `SupportUrl`

   選擇性的 `String` 參數。

   指定在啟動載入器安裝失敗時提供的 URL。

- `Validate`

   選擇性的 `Boolean` 參數。

   如果是 `true`，啟動載入器會在指定的輸入啟動載入器項目上執行 XSD 驗證。 此參數的預設值為 `false`。

## <a name="remarks"></a>備註
除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例
下列範例會使用 `GenerateBootstrapper` 工作來安裝必須安裝 .NET Framework 2.0 的應用程式。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
