---
title: MSBuild 屬性 | Microsoft Docs
description: 瞭解 MSBuild 名稱/值屬性組如何將值傳遞至工作、評估條件，以及儲存值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8f53613c71a51ab2e5bd8441cb4605da795e8a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897755"
---
# <a name="msbuild-properties"></a>MSBuild 屬性

屬性是名稱/值組，可以用來設定組建。 屬性可用於將值傳遞給工作、評估條件，以及儲存將在整個專案檔中參考的值。

## <a name="define-and-reference-properties-in-a-project-file"></a>定義和參考專案檔中的屬性

 宣告屬性的方式是建立具有屬性名稱的項目，做為 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 項目的子項目。 例如，下列 XML 會建立名為 `BuildDir` 並具有 `Build` 值的屬性。

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 在整個專案檔中，可使用語法 $(\<PropertyName>) 來參考屬性。 例如，使用 $(BuildDir) 來參考上述範例中的屬性。

 您可以藉由重新定義屬性來變更屬性值。 您可以使用下列 XML，為 `BuildDir` 屬性指定新值：

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 屬性會以其在專案檔中出現的順序來評估。 在指派舊值之後，必須宣告 `BuildDir` 的新值。

## <a name="reserved-properties"></a>保留的屬性

 MSBuild 保留一些屬性名稱來儲存專案檔和 MSBuild 二進位檔案的相關資訊。 這些屬性是使用 $ 標記法來參考，如同任何其他屬性。 例如，$(MSBuildProjectFile) 會傳回專案檔的完整檔名，包括副檔名。

 如需詳細資訊，請參閱 [如何：參考專案檔的名稱或位置](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) ，以及 [MSBuild 保留和已知的屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)。

## <a name="environment-properties"></a>環境屬性

 就像參考保留的屬性，您可以參考專案檔中的環境變數。 例如，若要在專案檔中使用 `PATH` 環境變數，請使用 $(Path)。 如果專案包含與環境屬性相同名稱的專案定義，則專案中的屬性會覆寫環境變數的值。

 每個 MSBuild 專案都有獨立的環境區塊：只會看見本身區塊中讀取和寫入的內容。  在評估或建立專案檔案之前，MSBuild 只會在初始化屬性集合時讀取環境變數。 在此之後，環境屬性會是靜態的，也就是說，每個繁衍的工具一開始都會採用相同的名稱和值。

 若要從衍生的工具內取得環境變數目前的值，請使用 GetEnvironmentVariable [屬性](../msbuild/property-functions.md) 。 然而，一般慣用的方法是使用工作參數 <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>。 這個字串陣列中設定的環境屬性可以傳遞至繁衍的工具，而不會影響系統環境變數。

> [!TIP]
> 並非所有環境變數都會在讀取後變成初始屬性。 會忽略任何未採用有效 MSBuild 屬性名稱 (例如 "386") 的環境變數。

 如需詳細資訊，請參閱 [如何：在組建中使用環境變數](../msbuild/how-to-use-environment-variables-in-a-build.md)。

## <a name="registry-properties"></a>登錄屬性

 您可以使用下列語法來讀取系統登錄值，其中 `Hive` 是登錄 hive (例如 **HKEY_LOCAL_MACHINE**) 、機碼名稱、子機 `MyKey` 碼名稱，以及子機碼的 `MySubKey` `Value` 值。

```xml
$(registry:Hive\MyKey\MySubKey@Value)
```

 若要取得預設的子機碼值，請省略 `Value`。

```xml
$(registry:Hive\MyKey\MySubKey)
```

 此登錄值可用來初始化建置屬性​​。 例如，若要建立一個建置屬性​​來代表 Visual Studio Web 瀏覽器首頁，請使用下列程式碼：

```xml
<PropertyGroup>
  <VisualStudioWebBrowserHomePage>
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)
  </VisualStudioWebBrowserHomePage>
<PropertyGroup>
```

## <a name="global-properties"></a>全域屬性

 MSBuild 可讓您使用 **-property** (或 **-p**) 參數，在命令列上設定屬性。 這些全域屬性值會覆寫專案檔中所設定的屬性值。 這包括環境屬性，但不包含保留的屬性，您無法變更後者。

 下列範例會將全域 `Configuration` 屬性設定為 `DEBUG`。

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 您也可以使用 MSBuild 工作的 `Properties` 屬性，針對多專案組建中的子專案設定或修改全域屬性。 除非使用 MSBuild 工作的 `RemoveProperties` 屬性指定不轉送屬性清單，否則全域屬性也會轉送至子專案。 如需詳細資訊，請參閱 [MSBuild](../msbuild/msbuild-task.md)工作。

 如果您使用專案標記中的 `TreatAsLocalProperty` 屬性 (Attribute) 指定屬性 (Property)，該全域屬性 (Property) 值就不會覆寫專案檔中設定的屬性 (Property) 值。 如需詳細資訊，請參閱 [ (MSBuild) 的專案專案 ](../msbuild/project-element-msbuild.md) 和 how [to：使用不同的選項建立相同的原始](../msbuild/how-to-build-the-same-source-files-with-different-options.md)程式檔。

## <a name="property-functions"></a>屬性函式

 從 .NET Framework 4 版開始，您可以使用屬性函式評估您的 MSBuild 指令碼。 您可以讀取系統時間、比較字串、比對規則運算式，以及執行組建指令碼中的其他動作，而不需使用 MSBuild 工作。

 您可以使用字串 (執行個體) 方法來操作任何屬性值，而且可以呼叫許多系統類別的靜態方法。 例如，您可以將建置屬性設為今天的日期，如下所示。

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 如需詳細資訊及屬性函式清單，請參閱 [屬性](../msbuild/property-functions.md)函式。

## <a name="create-properties-during-execution"></a>在執行期間建立屬性

 位於 `Target` 項目以外的屬性值是在組建的評估階段所指派。 在後續的執行階段，可以使用下列方式來建立或修改屬性：

- 任何工作均可發出屬性。 若要發出屬性，[Task](../msbuild/task-element-msbuild.md) 項目必須含有具 `PropertyName` 屬性的子系 [Output](../msbuild/output-element-msbuild.md) 項目。

- 透過 [CreateProperty](../msbuild/createproperty-task.md) 工作來發出屬性。 這種使用方式已過時。

- 從 .NET Framework 3.5 開始，`Target` 項目可能會包含 `PropertyGroup` 項目，其中可能包含屬性宣告。

## <a name="store-xml-in-properties"></a>將 XML 儲存於屬性中

 屬性可以包含任意的 XML，其有助於將值傳遞給工作，或是顯示記錄資訊。 下列範例示範 `ConfigTemplate` 屬性，其值會包含 XML 和其他屬性參考。 MSBuild 會使用其各自的屬性值來取代屬性參考。 屬性值是以其出現的順序來指派。 因此，在此範例中，應該已經定義 `$(MySupportedVersion)`、`$(MyRequiredVersion)` 及 `$(MySafeMode)`。

```xml
<PropertyGroup>
    <ConfigTemplate>
        <Configuration>
            <Startup>
                <SupportedRuntime
                    ImageVersion="$(MySupportedVersion)"
                    Version="$(MySupportedVersion)"/>
                <RequiredRuntime
                    ImageVersion="$(MyRequiredVersion)"
                    Version="$(MyRequiredVersion)"
                    SafeMode="$(MySafeMode)"/>
            </Startup>
        </Configuration>
    </ConfigTemplate>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [如何：在組建中使用環境變數](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [如何：參考專案檔的名稱或位置](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [如何：建立具有不同選項的相同原始檔案](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [MSBuild)  (Property 元素 ](../msbuild/property-element-msbuild.md)
