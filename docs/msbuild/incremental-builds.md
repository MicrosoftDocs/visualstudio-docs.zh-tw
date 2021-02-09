---
title: 累加組建 | Microsoft Docs
description: 深入瞭解 MSBuild 累加組建，其已優化，因此不會執行最新的輸出檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1237128852cec39ff49204e1c269f10153b42ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914080"
---
# <a name="incremental-builds"></a>累加組建

累加組建是已最佳化的組置，因此不會執行輸出檔案與其相關對應輸入檔案為最新的目標。 目標項目可能有 `Inputs` 屬性可指出目標預期作為輸入的項目，以及 `Outputs` 屬性可指出它產生作為輸出的項目。 MSBuild 嘗試尋找這些屬性值之間的 1 對 1 對應。 如果具有 1 對 1 對應，MSBuild 會比較每個輸入項目的時間戳記與其對應輸出項目的時間戳記。 沒有 1 對 1 對應的輸出檔案會與所有輸入檔案進行比較。 如果項目的輸出檔與輸入檔同齡或是前者較新，該項目則可視為最新狀態。

> [!NOTE]
> 當 MSBuild 評估輸入檔時，只會考慮目前執行中清單的內容。 最後一個組建清單中的變更不會自動將目標設為過期。

如果所有輸出項目都是最新的，則 MSBuild 會跳過目標。 目標的這個「累加組建」可以大幅改善建置速度。 如果只有某些檔案是最新的，則 MSBuild 會執行目標，但跳過最新項目，進而讓所有項目都具有最新狀態。 此程序稱為「部分累加組建」。

1 對 1 對應通常是透過項目轉換所產生。 如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。

 請考慮下列目標。

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

`Compile` 項目類型所代表的檔案集會複製至備份目錄。 備份檔案的副檔名為 *.bak*。 如果在執行備份目標之後未刪除或修改 `Compile` 項目類型所代表的檔案或對應的備份檔案，則會在後續組建中跳過備份目標。

## <a name="output-inference"></a>輸出推斷

MSBuild 會比較目標的 `Inputs` 和 `Outputs` 屬性，以判斷是否必須執行目標。 在理想情況下，不論是否執行相關聯的目標，累加組建完成之後存在的檔案集應該都會維持不變。 因為工作所建立或改變的屬性和項目可能會影響組建，所以 MSBuild 必須推斷其值，即使跳過影響它們的目標也是一樣。 此程序稱為「輸出推斷」。

有三種情況：

- 目標的 `Condition` 屬性評估為 `false`。 在此情況下，不會執行目標，而且對組建沒有任何作用。

- 目標的輸出過期，將會執行以使其具有最新狀態。

- 目標沒有過期輸出，將會予以跳過。 MSBuild 會評估目標並變更項目和屬性，就像已執行目標一樣。

若要支援累加編譯，工作必須確保任何 `Output` 項目的 `TaskParameter` 屬性值相當於工作輸入參數。 以下是一些範例：

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

不論執行還是跳過目標，此程式碼都會建立值為 "123" 的屬性 Easy。

從 MSBuild 3.5 開始，系統會自動對目標中的項目和屬性群組執行輸出推斷。 目標中不需要 `CreateItem` 工作，應該予以避免。 此外，只應該在目標中使用 `CreateProperty` 工作，以判斷是否已執行目標。

在 MSBuild 3.5 以前，您可以使用 [CreateItem](../msbuild/createitem-task.md) 工作。

## <a name="determine-whether-a-target-has-been-run"></a>判斷是否已執行目標

基於輸出推斷，您必須新增目標的 `CreateProperty` 工作來檢查屬性和項目，以判斷是否已執行目標。 將 `CreateProperty` 工作新增至目標，並為它提供其 `TaskParameter` 為 "ValueSetByTask" 的 `Output` 項目。

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

此程式碼會建立 CompileRan 屬性，並為其提供 `true` 值，唯一前提是已執行目標。 如果跳過目標，則不會建立 CompileRan。

## <a name="see-also"></a>另請參閱

- [目標](../msbuild/msbuild-targets.md)
